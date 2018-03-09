# Pose Guided Person Image Generation (NIPS 2017)

This is an unofficial implementation. The paper's author Liqian Ma has released his version at https://github.com/charliememory/Pose-Guided-Person-Image-Generation.




# Clone this repository
```
git clone https://github.com/samuelzhouhe/poseGuidedImgGeneration.git
cd poseGuidedImgGeneration
```

# Install pip3
```sudo apt-get install python3-pip python3-dev```

# Install all required libraries
```pip3 install -r requirements.txt```

# Download dataset and keypoints (Please observe all requirements set by the dataset owner)
Download the dataset DeepFashion from http://mmlab.ie.cuhk.edu.hk/projects/DeepFashion.html
Then put the folder In-shop Clothes Retrieval Benchmark in the project directory, and then rename this directory to 'dataset'.
Then download the keypoint locations prepared by us (using OpenPose, CVPR2017) from https://drive.google.com/file/d/1DwRPXCyVYBmtGa0hO3JlYkrD709s6zca/view?usp=sharing, put it inside the directory dataset/, and extract it.
Your dataset directory should look like this:
poseGuidedImageGeneration
---dataset
------Anno
------Eval
------Img
---------img
---------img-keypoints


# Use pre-trained model
Download model.tar.gz from https://drive.google.com/file/d/1z0mtWRSy_ObQ5NfXwXwcT9mIipIPxBsY/view?usp=sharing to project folder, then:
```
tar -xvzf model.tar.gz
rm -rf logs
mv model logs
python3 demo.py
```
# Train from scratch
```
rm -rf logs
command: python3 trainall.py
```

# Descriptions of source files

config.py: parameters used for our network

dataset_reader.py: load training image data batches and process them for training

model_all.py: build G1, G2 & D in TensorFlow

network.py: helper class for building complicated networks

read_keypoint.py: adopt keras realtime multi-person pose estimation model to produce heatmap of human poses

trainall.py: the main training procedure

demo.py: use the pre-trained model to demo our result

dataset/: the directory which contain a small subset of the DeepFashion dataset. The full dataset is too large to submit, and we've signed an use agreement with the DeepFashion team so we did not upload all of the data.

System tested: Linux (Ubuntu)
