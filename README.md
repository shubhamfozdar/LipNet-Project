# LipNet-Project
Building a Machine Learning Model that's able to perform lip reading.

The modeules used and the process to be follwed is attatched below:-

<h3>0. Install and Import Dependencies</h3>

**OpenCV-Python**:-  OpenCV-Python serves as a valuable tool in the LipNet project for various tasks ranging from preprocessing and feature extraction to visualization and debugging, ultimately contributing to the development of an accurate and robust lip reading system.

**Matplotlib**:-   Matplotlib complements OpenCV-Python in the LipNet project by providing capabilities for data visualization, model performance evaluation, feature analysis, debugging, and analysis, thus enhancing the development and understanding of the lip reading system.

**imageio**:- imageio serves as a versatile tool for handling video input/output operations in the LipNet project, facilitating tasks such as video loading, saving, format conversion, frame extraction, and real-time video processing. Its capabilities complement other libraries like OpenCV and Matplotlib, contributing to the efficient development and deployment of the lip reading system.

**gdown**:-  gdown simplifies the process of downloading datasets and pre-trained models from Google Drive, streamlining the development and experimentation process in the LipNet project for lip reading using machine learning.

**Tensorflow**:- TensorFlow serves as a powerful framework for developing, training, and deploying deep learning models in the LipNet project, facilitating tasks such as model development, training, transfer learning, inference, performance optimization, and research experimentation. Its rich ecosystem of tools and resources empowers researchers and developers to build accurate and efficient lip reading systems using state-of-the-art deep learning techniques.

<br>
<h3>1. Build Data Loading Functions</h3>
This Python function load_video loads a video file specified by the path parameter. Let's break down the steps:

1. It initializes a **'VideoCapture'** object **'cap'** using OpenCV's **'cv2.VideoCapture'** function, passing the provided **'path'**.

2. It initializes an empty list **'frames'** to store the frames of the video.

3. It iterates over the number of frames in the video, which is obtained using cap.get(cv2.CAP_PROP_FRAME_COUNT). For each iteration:

* It reads the next frame from the video using cap.read(). The return value ret indicates whether a frame was successfully read, and frame holds the actual frame data.
* It converts the frame from RGB to grayscale using TensorFlow's tf.image.rgb_to_grayscale function.
* It selects a specific region of interest (ROI) from the frame using array slicing (frame[190:236,80:220,:]) and appends it to the frames list. This seems to be cropping the frame to a specific area.
After reading all frames, it releases the video capture object using cap.release() to free up system resources.

It calculates the mean and standard deviation of the pixel values across all frames using TensorFlow's tf.math.reduce_mean and tf.math.reduce_std functions respectively.

It normalizes the pixel values of all frames by subtracting the mean and dividing by the standard deviation. This normalization helps in improving the stability and convergence of machine learning algorithms.

It returns the normalized frames as a TensorFlow tensor with tf.cast((frames - mean), tf.float32) / std.

Overall, this function loads a video, preprocesses its frames by converting them to grayscale and cropping a specific region, normalizes the pixel values, and returns them as a TensorFlow tensor. 
