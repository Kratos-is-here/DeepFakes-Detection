# DeepFakes-Detection

## My Approach -

- We take 15 uniformly time-spaced frames from the video and work upon them.
- Then we crop out the area around the person's face in each frame using the RetinaFace module.
- [RetinaFace](https://github.com/serengil/retinaface#:~:text=RetinaFace%20is%20a%20deep%20learning,is%20mainly%20based%20on%20mxnet) performs pixel-wise face localisation on various scales of faces by taking advantages of joint extra-supervised and self-supervised multi-task learning. RetinaFace outperforms the state of the art average precision (AP) by 1.1% 
- We use Retina-Face with Resnet-50 as the encoder model.
- After getting the cropped face we normalizing it and resize every pictures to (320,320,3) shape, i.e. an rgb image of 320px * 320px
- We finally use an ensemble of Efficient-Net and Xception net by getting there predictions as probabilites and then try out different ratios for the both of them.
- The best ratio was with giving 30% weightage to the xception model's score and 70% to the efficient net model.

## Results
- This model acheived 2nd place in the [DeepFake Detection Challenge hosted on Kaggle](https://www.kaggle.com/competitions/deepfake-detection/overview)
- F1 Score on the testing dataset = 0.93589
