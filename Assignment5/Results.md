Gender: 92.29 <br/>
ImageQuality: 55.82 <br/>
Age: 46.12 <br/>
Weight 66.03 <br/>
Bag: 69.71 <br/>
Footwear: 67.82 <br/>
Pose: 87.35 <br/>
Emotion: 71.22 <br/>

Epoch 40/100
360/360 [==============================] - 290s 807ms/step - loss: 3.6375 - gender_output_loss: 0.0968 - image_quality_output_loss: 0.5430 - age_output_loss: 0.7900 - weight_output_loss: 0.4896 - bag_output_loss: 0.3837 - footwear_output_loss: 0.4466 - pose_output_loss: 0.1430 - emotion_output_loss: 0.7447 - gender_output_acc: 0.9622 - image_quality_output_acc: 0.7816 - age_output_acc: 0.6684 - weight_output_acc: 0.8138 - bag_output_acc: 0.8530 - footwear_output_acc: 0.8176 - pose_output_acc: 0.9486 - emotion_output_acc: 0.7412 - val_loss: 7.9810 - val_gender_output_loss: 0.3082 - val_image_quality_output_loss: 1.3225 - val_age_output_loss: 1.6143 - val_weight_output_loss: 1.1582 - val_bag_output_loss: 1.1369 - val_footwear_output_loss: 1.0082 - val_pose_output_loss: 0.5228 - val_emotion_output_loss: 0.9099 - val_gender_output_acc: 0.9229 - val_image_quality_output_acc: 0.5582 - val_age_output_acc: 0.4612 - val_weight_output_acc: 0.6603 - val_bag_output_acc: 0.6971 - val_footwear_output_acc: 0.6782 - val_pose_output_acc: 0.8735 - val_emotion_output_acc: 0.7122

<h1>Methodology</h1>
Change Different models: 
Tried with inceptionv3, resnet52V2, resnetinception, densenet121, Initial models were stagnating after time, 
and densenet was overfitting and not able to control 

First Bug Encountered: No Normalization 
Second Bug: PersonDataGenerator was not correct for valid_gen
Third Issue: Achieved closed to 99% but later to be found that it was because of data leak 

Tried ImageDataGenerator, Then moved to imgaug, also tried Albumentations 

For LR, I tried step lr, then cyclic lr with range test, 
Ran for 180 epochs, logs are present in [epochlogs](https://github.com/ankush2805/EIP/blob/master/Assignment5/EpochLogs.txt)
https://github.com/ankush2805/EIP/blob/master/Assignment5/EpochLogs.txt

Actual code can be found at [code](https://github.com/ankush2805/EIP/blob/master/Assignment5/PersonAttributes_Resnet152V2_IMGAUG_CYCLIC_LR_FINAL.ipynb)
https://github.com/ankush2805/EIP/blob/master/Assignment5/PersonAttributes_Resnet152V2_IMGAUG_CYCLIC_LR_FINAL.ipynb
