# Experiment 2: Image Acquisition Using Web Camera

## Aim

To acquire images and video frames using a webcam and perform basic image processing operations such as displaying, resizing, and rotating captured frames using Python, OpenCV, and Matplotlib.

## Objectives

- To initialize and access a webcam using OpenCV.
- To capture and save an image frame from the webcam.
- To read and display the captured image.
- To acquire and display consecutive webcam frames.
- To resize captured frames to specified dimensions.
- To rotate webcam frames by 90 degrees clockwise.
- To understand BGR-to-RGB color conversion for image visualization.

## Software Requirements

- Python 3.x
- OpenCV
- Matplotlib
- Jupyter Notebook
- Working webcam

## Algorithm

1. Start the program.
2. Import the required libraries: OpenCV, Matplotlib, IPython display utilities, and time.
3. Initialize the webcam using `cv2.VideoCapture(0)`.
4. Capture a frame using the `read()` method.
5. Save the captured frame as an image file.
6. Release the webcam and load the saved image.
7. Convert the image from BGR to RGB and display it using Matplotlib.
8. Reopen the webcam and capture consecutive frames.
9. Convert each frame to RGB and display it.
10. Resize each captured frame to the specified dimensions and display it.
11. Rotate each captured frame by 90 degrees clockwise and display it.
12. Release the webcam after each operation.
13. Stop the program.

## Program

### 1. Import Required Libraries

```python
import cv2
import matplotlib.pyplot as plt
from IPython.display import clear_output
import time
```

### 2. Capture and Save an Image

```python
cap = cv2.VideoCapture(0)

ret, frame = cap.read()

if ret:
    cv2.imwrite("captured_frame.jpg", frame)

cap.release()
```

### 3. Read and Display the Captured Image

```python
captured_image = cv2.imread("captured_frame.jpg")

plt.imshow(captured_image[:, :, ::-1])
plt.title("Captured Frame")
plt.axis("off")
plt.show()
```

### 4. Display Consecutive Webcam Frames

```python
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()

    if not ret:
        break

    frame_rgb = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)

    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.axis("off")
    plt.show()

    time.sleep(0.05)

cap.release()
```

### 5. Resize Webcam Frames

```python
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()

    if not ret:
        break

    resized_frame = cv2.resize(frame, (100, 150))
    frame_rgb = cv2.cvtColor(
        resized_frame, cv2.COLOR_BGR2RGB
    )

    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.axis("off")
    plt.show()

    time.sleep(0.05)

cap.release()
```

### 6. Rotate Webcam Frames

```python
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()

    if not ret:
        break

    rotated_frame = cv2.rotate(
        frame, cv2.ROTATE_90_CLOCKWISE
    )

    frame_rgb = cv2.cvtColor(
        rotated_frame, cv2.COLOR_BGR2RGB
    )

    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.axis("off")
    plt.show()

    time.sleep(0.05)

cap.release()
```

## Result

Thus, image acquisition using a webcam was performed successfully. An image was captured and saved, consecutive frames were displayed, and webcam frames were resized and rotated using OpenCV and Matplotlib.
