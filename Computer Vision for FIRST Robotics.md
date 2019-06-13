# Computer Vision for _FIRST_ Robotics

![AA](assets\AA.png)


### Aims

* Learn to do basic Computer Vision (CV) operations
* Develop a system for intelligent analysis of a scene
* Learn how to find the resources to develop further CV skills

### Resources
*    [OpenCV tutorials](https://docs.opencv.org/3.0-beta/doc/py_tutorials/py_tutorials.html)
*  [PyCharm IDE](https://www.jetbrains.com/pycharm/) or OCVID (if ready)   
*   Aerial Assist Final footage.

### Overview
1.  Learn how to load and view images and frames from a video
2.  Understand the structure of images through basic operations (grayscale etc)
3.  ROI selection
4.  Basic colour segmentation
5.  Basic shape detection
6.  Object tracking
7.  Score detection!

### Interdisciplinary opportunities
None…?

***

## Introduction

### What is Computer Vision?

![Computer vision example 1](assets\1560329040581.png)

One of the main ways humans can tell what’s happening around them is through sight, and it’s one of the most useful (but difficult) tools for a computer to use. Robotics in particular relies heavily on vision to interact appropriately with the world.

![Computer vision example 2](assets\1560329054326.png)

Specifically, Computer Vision is a discipline within computer science which concerns itself with algorithms to derive meaning from camera inputs, and includes powerful techniques like image classification (understanding what’s in a photo), photogrammetry (constructing 3d scenes from multiple images), facial recognition, and many more.


#### What is OpenCV?

![OpenCV and Python](assets\1560329069586.png)In the same way that engineers use off-the-shelf parts rather than machining them from scratch, programmers use pre-built libraries to shortcut the difficult task of implementing tools from scratch. OpenCV is a publicly available library designed to make computer vision quick and easy, and is both well documented and heavily used. OpenCV is available with C++, Python and Java bindings, but for this tutorial we will be using Python, since it makes very simple code.

Throughout this tutorial, you can find more information on any topic in the footnotes, or do your own search - some great resources can be found in the [opencv python tutorials](https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_tutorials.html)


### Why are we doing this?
_FIRST_ Robotics Competition encourages students to develop cutting-edge robotics, but a robot without sensing and processing is little more than a remote controlled car. Integrating computer vision in your robot makes it far more effective on the field, and can help the robot make decisions when the driver can’t see well or react quickly enough.

There are many things a robot with computer vision can do, including (but not limited to):

-   Goal & game element identification
-   Visual servoing (automatically reaching a target)
-   Auto-aim
-   Auto-align
-   Field mapping

### OK, what do I do?
The following steps will take you through the techniques to achieve a complex computer vision task, building up advanced algorithms using basic building blocks. Follow along with the steps, making sure you write out all provided code and explore options wherever possible. Throughout the process, keep in mind what else you could use each concept for. Also, make sure to comment your code as required to help jog your memory later, and continually save and back up your code using Git by following the prompts -- that way, you can refer back to the code in future whenever you have to do a similar task, since you already have working code!

**Note:** For the duration of this tutorial, the code will be explained in detail but I will assume you have some knowledge about python programming; if you have never used it before, you will have a slightly harder time understanding what is happening. If you want to quickly pick up some basics to make it easier to read, I recommend flicking through the [Codecademy tutorial](https://www.codecademy.com/learn/learn-python-3). This is a free interactive tutorial that covers basic syntax, although you will have to create an account.
## Setup

### How do I get started?

There are a few things you have to do to set up this project. It will take a little while, but these steps apply to any project you might want to do in the future - setting up the git repository and development environment properly is worth putting time into, since it makes everything else easier.

### Set up Git

As a programmer, you should get into the habit of using Git for all your projects. This gives you a cloud based backup of your code so you can always access it, and creates a history of code -- like the ultimate Ctrl+Z!

Throughout this tutorial, you will see prompts to help you keep up your git repository. If you follow these carefully, your git repository will be set up well and your code will be saved for later use! Make sure you read the descriptions of what you’re doing whenever a new command is introduced, so you know what’s going on.

To start with, go to [https://github.com/new](https://github.com/new) and either sign in to github (if you have an account) or create a new account. Github is a free online code hosting platform which is extremely handy for programmers. Once you’ve signed in, you should see the below screen; make sure you give it a good name, description and tick the box for a README, then click “Create repository”.

![Create a repo!](assets\1560328920215.png)

Once you’ve created your repository online, you want to create a local copy where you can edit your code. To interact with Git locally, you have to install Git on your computer; just go to [https://git-scm.com/book/en/v2/Getting-Started-Installing-Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and follow the instructions for your operating system. You’ll then have access to terminal commands for interacting with git - on Windows, this is called “git bash”, while on Linux and Mac you can type these commands directly into the terminal.

```git
git clone https://github.com/<username>/computer-vision-tutorial
git status 
```
> On windows, shift-rightclick in the directory you want the project in, and select “open git bash here”. ( Otherwise open the terminal and navigate to the directory ).
> You run all git commands by typing “git” followed by a particular command -- type “git help” to see all of them. To understand them better, google is your friend!


### Install Python and IDE

One of the things you’ll need to follow this tutorial (of course) is the Python programming language. If you do not already have it on your computer, go to [https://www.python.org/downloads/](https://www.python.org/downloads/) and get the latest version.

You can develop python code using any approach you could use to write a text file, but it’s a lot easier if you have an Integrated Development Environment (IDE) - this is a program which helps you write and run code easily. For python, there are many options for this, but I recommend Jetbrains PyCharm; you can get a free version from [https://www.jetbrains.com/pycharm/](https://www.jetbrains.com/pycharm/). Other IDEs that work include Microsoft Studio Code, Anaconda Spyder, or Python IDLE, and a quick google search will find a dozen more, so it’s easy to find one that suits your taste.

Open up your IDE and create a file called `main.py`; inside this file, type this line:

```python
print("Hello, Python!")
```

main.py

Then, use your IDE to run this file, and you should see the phrase appear in a console window. If not, you’ll need to figure out why, since your python needs to be set up correctly to run this tutorial.

### Add requirements

The key feature of Python is the abundance of libraries available for development, including OpenCV.  In order to define and install the libraries we need here, create a file in your project directory called “requirements.txt”, and fill it with this content:

```python
python-opencv
numpy
```
requirements.txt

Most python IDEs have a way to handle this file; if you’re using PyCharm, go to <https://www.jetbrains.com/help/pycharm/managing-dependencies.html> and follow the instructions for how to load the libraries, otherwise google your IDE to find out how to handle the requirements file properly. 

```git
git status
git add main.py requirements.py
git commit -m"Started project, defined requirements"
git push
```

> Saving changes in git requires three separate steps:
>
> * “add” tells git which files you want to save.  “git add .” adds all changes.
> *  “commit” is the actual save - it creates a checkpoint with a description for later.
>
> *  “push” uploads all your commits to github



### Preparing the task

The task we’ll be building up to in this tutorial is to automatically score an FRC match - specifically, the final Einstein match from the 2014 game, Aerial Assist.

In this game, points were scored when the game elements were thrown into the goals at either end of the field, tossed over the central truss, or passed between robots.

![img](assets\AA.png)

To prepare, you’ll need an image and a video file to test with; please download files from <ADD LINK> and <ADD LINK>, and copy them into your project directory.

```git
git add AA.png AA.mp4
git commit -m"Added data files"
git push
```

> In this case, we’re committing the data files; however, you should generally avoid putting data in your git repository, as large files can fill up your git repo very fast.
>
> We’re doing it here because the files aren’t huge and for demonstration purposes.

OK, you’re now ready to write some code!

## OpenCV basics

Obviously, the most important thing you have to be able to do when working with images is open and view images.  

Open the main.py file and add these lines:

```python
import cv2

frame = cv2.imread("AA.png")
cv2.imshow("output", frame)
cv2.waitKey(0)
```

main.py

What does this code do?

- `import cv2`: brings in the opencv library into your code, allowing it to be used.  Now, all the functions available in the opencv python bindings can be accessed using “cv2.”  Throughout this tutorial, this line should always be at the top of your code.
- `frame = cv2.imread (“AA.png”)`: reads the specified file and stores it in the “frame” variable as an array.
- `cv2.imshow(“output”, frame)`: opens up a window for you to see the image you provide it.  `“output”` is the title of the window.
- `cv2.waitKey(0)`: This line tells the code to wait until you press a key before moving on; if you don’t do this, the frame will disappear immediately after opening.  If you change the `0` to any other positive number, it will wait that many milliseconds before moving on if you don’t press a button.

OK, looking at pictures is one thing, but videos are really where it’s at.  Videos allow you to test a lot of images very quickly, and even use the time between frames to make decisions.

To open and view a video, change the code to the following:

```python
import cv2

cap = cv2.VideoCapture('AA.mp4')

while(True):
    # Capture frame-by-frame
    _, frame = cap.read()
    # Display the resulting frame
    cv2.imshow("output", frame)
```

main.py

In this code, we see the “VideoCapture” object -- once created, you can read one frame at a time using the `cap.read()` function.

Notice that this time round, we don’t need the `cv2.waitKey` function, since we don’t actually want it to pause after every frame.  However, we want some basic control of the video playback, so add the following lines:

```python
...
	cv2.imshow("output", ret)
    key = cv2.waitKey(1)
    if key & 0xFF ord('p'):
		key = cv2.waitKey(0)
	if key & 0xFF == ord('q'):
		break
```

main.py

There are simpler ways to do this, but this code gives you a “pause” key (p) and a “quit” key (q), so you can freeze on a frame or end the program.

Note the `waitKey(1)` here - as described above, this tells the code to wait for 1ms before moving on.  If you make this number bigger, the video will run slower, which might be helpful so you can see each frame more clearly.

```git
git add main.py
git commit -m"Implemented basic read/show"
git push
```

> Doing these steps regularly might begin to feel tedious, but it’s absolutely worth doing every time you finish a step, as this allows you to return to this stage in your project whenever you want.  I will suggest times to do this throughout, but feel free to do it more often - just make sure you always write a descriptive message.

### Basic operations

> ### Sidenote!
> One thing you need to wrap your head around is how Python sees your image.
> The image below demonstrates how the image is represented digitally - it’s stored as a matrix of 8 bit integers (0-255, whole numbers) which represent the brightness of each point in the image (pixel).  ![img](assets\pasted image 0.png)
>
> It gets a little bit more complicated for colour images, but not much - instead of a single number, each pixel is then represented by a triplet of 8 bit integers, e.g. (255, 0, 127).  Each number represents the brightness of one component of colour in that pixel.  By default, OpenCV uses BGR colour format, which means the first number represents Blue, the second represents Green and the third represents Red.  What colour does the example triplet represent?

Just viewing images is not very useful - let’s start changing them now!

The first thing we’ll do is add an annotation to the picture - putting some text in the corner.  Add the below line to your main.py; can you figure out where to place the line?  Keep in mind that the frame has to be defined, and it will only have the annotation after this line runs.

```python
cv2.putText(frame, 'Hello!', (10,50), cv2.FONT_HERSHEY_SIMPLEX, 2, (255,255,0), 8)
```

main.py

This line is a little complicated, but have a play with the different parameters:

- The third parameter [(10,50)] is the location in the image of the bottom left corner of the text.
- The fourth parameter is the font face - if your IDE has python autocomplete, type “cv2.FONT_” and see what it suggests!
- The fifth parameter (2) is the scale of the text (it’s actually a scale multiplier applied to the “base size” of the given font.
- The sixth parameter is the font colour, defined as a BGR triplet as described above.
- The seventh parameter is the thickness of the lines used to draw the text



Hopefully, you figured out where that line should go.  However, as we move forward and add many more operations, it can get a lot more complicated to figure out.  So before we move on, let’s restructure our code to make it easier to extend by separating it into functions:



```python
import cv2

def processFrame(frame):
    ret = addAnnotation(frame)
    return ret

def addAnnotation(frame):
   cv2.putText(frame, 'Hello!', (10,50), cv2.FONT_HERSHEY_SIMPLEX, 2, (255,255,0), 8)
   return frame

cap = cv2.VideoCapture('AA.mp4')

while(True):
   # Capture frame-by-frame
   _, frame = cap.read()
   ret = processFrame(frame)
   # Display the resulting frame
   cv2.imshow('output',ret)
   key = cv2.waitKey(1)
   if key & 0xFF ord('p'):
       key = cv2.waitKey(0)
   if key & 0xFF == ord('q'):
       break
```

main.py

So, the “main” part of the code (the part which is actually run) is at the bottom, with no indent; we shouldn’t have to change this part from now on.  Instead, we’ll change the “processFrame” function - we just have to make sure that function always returns an OpenCV image.  

```git
git add main.py
git commit -m"Restructured code"
git push
```




Now, let's convert the image to grayscale.

```python
def processFrame(frame):
    ret = BGRtoGrayscale(frame)
    return ret

def BGRtoGrayscale(frame):
    return cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
```

main.py

The image you see should now be in black and white instead of colour!


Due to the way we've structured our code, we can combine multiple functions in `processFrame`:

```python
def processFrame(frame):
    gray = BGRtoGrayscale(frame)
    ret = addAnnotation(gray)
    return ret
```

main.py

You should notice that when you run this code, the output frame does **not** have a coloured annotation - because you add the annotation to a grayscale image, the colour is converted to grayscale before OpenCV draws the text.  In order to draw coloured text on a grayscale image (or, any coloured shape, as you'll see later), you have to first convert the grayscale back into colour:

```python
def processFrame(frame):
    gray = BGRtoGrayscale(frame)
    bgr = GrayscaleToBGR(gray)
    ret = addAnnotation(bgr)
    return ret

def GrayscaleToBGR(gray):
	return cv2.cvtColor(frame, cv2.COLOR_GRAY2BGR)
```
main.py


![img](assets\pasted image 0-1560333812393.png)

What's the point of doing this?  Just to get some practice manipulating images in OpenCV.  Later we'll see other colour spaces that are more useful.

```git
git add main.py
git commit -m"Added grayscale and annotations"
```

## Region of Interest

The video we're using includes a lot of content which is not useful to us - tracking the people in the background won't help calculate the score!

However, the camera is fixed, so the part of the image we care about (i.e. the field) is always in the same place.  So, what we can do is define a so-called <abbr title="Region (or Rectangle) of Interest">ROI</abbr>.  By doing this, we can tell OpenCV which part of the image we care about.

> If you were using this for a robot

### Rectangular

```python
import cv2
import numpy as np

def processFrame(frame):
   field = rectROI(frame)
   return field

def rectROI(frame):
   ret = frame[200:450,20:800]
   return ret
```

main.py

What's happening here? 

This uses a very simple approach for ROI extraction; we simply define a variable called `ret` which gets all the data from `frame`, but only between rows 200 and 450, and columns 20 to 800. 

![img](assets\pasted image 0-1560335029941.png)

Obviously, this is a very simple approach, and it can work very well.  However, there are two potential issues for our use case:

* Our view of the field is not actually rectangular
* Due to perspective, the ball can actually jump out of this rectangle; we may want to track it above the truss without including all those rows.

The solution to this problem is to use a more complex shape for the contour.

### Concave





