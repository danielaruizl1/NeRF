# Face Recognition

This package offers a ROS service that allows the robot to recognize people.

## Table of contents

- [Installation](#Installation).
- [Execution](#Execution).

## Installation
### Requirements
- Linux Ubuntu 18.04 or 20.04
- ROS Melodic or ROS Noetic (respectively)
- Python >= 2.7

### Installing
1. Get in your workspace and clone the repository
<pre><code>git clone https://github.com/SinfonIAUniandes/perception_tools.git
</code></pre>

2. Build the workspace
<pre><code>catkin_make
source devel/setup.bash
</code></pre>

## Execution
### Requirements

It is necessary that you have the encodings of people you want to recognize in a file named "face_enc". To do that, do you need to create a folder named "dataset" where you have subfolders with photos for each one of the people you want to train the model for. Later, run the following line:
<pre><code>python features_extraction.py
</code></pre>

### Executing
1. Activate roscore
2. Run the following line:
<pre><code>rosrun perception_package main_node_face.py
</code></pre>

