Code1:
Initially when we started, we were using less number of layers and directly apply large kernal to get output which was wrong

Code2: 
We properly added 2 layers of convolution followed by a layer of maxpooling and repeated the number of steps till the size of
was less and latter flattened and applied softmax, We were able to acheive required accuracy but number of paramters was high, 
So first step was to reduce number of paramters

Code3:
How do we reduce number of params, by changing the number of kernels we are expanding with, so now we have less paramters,
which fulfils less paramters but decreases the accuracy, lets increase that now 

Code 4: 
One way of increasing is by using batch normalization, it will help in training the network faster and also help in reducing 
covariant shift. ALso it helps the network to reach gloabl minima. But BN doesnot work well with Nmist and doesnot provide
increasing the accuracy

Code 5: 
We currently are near 11k params, and since limit is 15, we still have room for changing kernel size, lets give it a bit bump,
One other thing we added is validation accuracy, So we donot just depend on the last epoch accuracy , Naah!! Still 
we habe not achieved desired accuracy, 

Code 6: 
One thing we notice that we are seeing huge diff in val score and train score, which means we are seeing regularization
problem, Lets do it, So we add dropout, we can add l1 and l2 regularization also

Code 7:
But one thing we notice is our val score in bumping up and down, and we know how manage this, we will apply learning rate 
so this jumping up and down can be controlled.

Code8 :
SO we have achieved the desired accuracy lets slowly reduce kernel parameters and check , so we bring it to 16

Code 9:
Approach 1: We trim down size of 1 layer, and try to acheive accuracy, also we remove drop out and BN at the last layer as
we have almost gathered all the info, We will hit high accuracy
Approach 2: While researching came across seprable conv2d which helps with higher kernel size and less number of params, 
Used it, but then overfitting was happening so added drop out which helped in acheiving accuracy


With Approach 1

Train on 60000 samples, validate on 10000 samples
Epoch 1/20

Epoch 00001: LearningRateScheduler setting learning rate to 0.003.
60000/60000 [==============================] - 46s 773us/step - loss: 0.1657 - acc: 0.9478 - val_loss: 0.0606 - val_acc: 0.9795
Epoch 2/20

Epoch 00002: LearningRateScheduler setting learning rate to 0.0022744503.
60000/60000 [==============================] - 38s 637us/step - loss: 0.0661 - acc: 0.9792 - val_loss: 0.0518 - val_acc: 0.9832
Epoch 3/20

Epoch 00003: LearningRateScheduler setting learning rate to 0.0018315018.
60000/60000 [==============================] - 38s 640us/step - loss: 0.0545 - acc: 0.9833 - val_loss: 0.0286 - val_acc: 0.9904
Epoch 4/20

Epoch 00004: LearningRateScheduler setting learning rate to 0.0015329586.
60000/60000 [==============================] - 38s 638us/step - loss: 0.0457 - acc: 0.9857 - val_loss: 0.0278 - val_acc: 0.9917
Epoch 5/20

Epoch 00005: LearningRateScheduler setting learning rate to 0.0013181019.
60000/60000 [==============================] - 38s 636us/step - loss: 0.0411 - acc: 0.9868 - val_loss: 0.0301 - val_acc: 0.9910
Epoch 6/20

Epoch 00006: LearningRateScheduler setting learning rate to 0.0011560694.
60000/60000 [==============================] - 39s 645us/step - loss: 0.0364 - acc: 0.9886 - val_loss: 0.0255 - val_acc: 0.9923
Epoch 7/20

Epoch 00007: LearningRateScheduler setting learning rate to 0.0010295127.
60000/60000 [==============================] - 38s 637us/step - loss: 0.0324 - acc: 0.9898 - val_loss: 0.0270 - val_acc: 0.9910
Epoch 8/20

Epoch 00008: LearningRateScheduler setting learning rate to 0.0009279307.
60000/60000 [==============================] - 38s 636us/step - loss: 0.0319 - acc: 0.9899 - val_loss: 0.0215 - val_acc: 0.9934
Epoch 9/20

Epoch 00009: LearningRateScheduler setting learning rate to 0.0008445946.
60000/60000 [==============================] - 38s 640us/step - loss: 0.0293 - acc: 0.9907 - val_loss: 0.0217 - val_acc: 0.9933
Epoch 10/20

Epoch 00010: LearningRateScheduler setting learning rate to 0.0007749935.
60000/60000 [==============================] - 38s 639us/step - loss: 0.0284 - acc: 0.9906 - val_loss: 0.0252 - val_acc: 0.9926
Epoch 11/20

Epoch 00011: LearningRateScheduler setting learning rate to 0.0007159905.
60000/60000 [==============================] - 38s 639us/step - loss: 0.0257 - acc: 0.9917 - val_loss: 0.0280 - val_acc: 0.9918
Epoch 12/20

Epoch 00012: LearningRateScheduler setting learning rate to 0.000665336.
60000/60000 [==============================] - 38s 635us/step - loss: 0.0271 - acc: 0.9912 - val_loss: 0.0214 - val_acc: 0.9936
Epoch 13/20

Epoch 00013: LearningRateScheduler setting learning rate to 0.0006213753.
60000/60000 [==============================] - 38s 640us/step - loss: 0.0227 - acc: 0.9927 - val_loss: 0.0223 - val_acc: 0.9928
Epoch 14/20

Epoch 00014: LearningRateScheduler setting learning rate to 0.0005828638.
60000/60000 [==============================] - 39s 646us/step - loss: 0.0231 - acc: 0.9926 - val_loss: 0.0206 - val_acc: 0.9934
Epoch 15/20

Epoch 00015: LearningRateScheduler setting learning rate to 0.0005488474.
60000/60000 [==============================] - 38s 637us/step - loss: 0.0212 - acc: 0.9933 - val_loss: 0.0188 - val_acc: 0.9938
Epoch 16/20

Epoch 00016: LearningRateScheduler setting learning rate to 0.0005185825.
60000/60000 [==============================] - 38s 634us/step - loss: 0.0208 - acc: 0.9933 - val_loss: 0.0213 - val_acc: 0.9933
Epoch 17/20

Epoch 00017: LearningRateScheduler setting learning rate to 0.000491481.
60000/60000 [==============================] - 38s 639us/step - loss: 0.0214 - acc: 0.9932 - val_loss: 0.0206 - val_acc: 0.9942
Epoch 18/20

Epoch 00018: LearningRateScheduler setting learning rate to 0.0004670715.
60000/60000 [==============================] - 38s 638us/step - loss: 0.0192 - acc: 0.9939 - val_loss: 0.0170 - val_acc: 0.9943
Epoch 19/20

Epoch 00019: LearningRateScheduler setting learning rate to 0.0004449718.
60000/60000 [==============================] - 38s 637us/step - loss: 0.0200 - acc: 0.9939 - val_loss: 0.0217 - val_acc: 0.9937
Epoch 20/20

Epoch 00020: LearningRateScheduler setting learning rate to 0.000424869.
60000/60000 [==============================] - 38s 638us/step - loss: 0.0190 - acc: 0.9937 - val_loss: 0.0216 - val_acc: 0.9934
 
 With Approach 2
 Train on 60000 samples, validate on 10000 samples
Epoch 1/20

Epoch 00001: LearningRateScheduler setting learning rate to 0.003.
60000/60000 [==============================] - 49s 823us/step - loss: 0.1475 - acc: 0.9556 - val_loss: 0.0448 - val_acc: 0.9851
Epoch 2/20

Epoch 00002: LearningRateScheduler setting learning rate to 0.0022744503.
60000/60000 [==============================] - 39s 657us/step - loss: 0.0569 - acc: 0.9818 - val_loss: 0.0331 - val_acc: 0.9894
Epoch 3/20

Epoch 00003: LearningRateScheduler setting learning rate to 0.0018315018.
60000/60000 [==============================] - 41s 679us/step - loss: 0.0456 - acc: 0.9858 - val_loss: 0.0288 - val_acc: 0.9913
Epoch 4/20

Epoch 00004: LearningRateScheduler setting learning rate to 0.0015329586.
60000/60000 [==============================] - 40s 675us/step - loss: 0.0394 - acc: 0.9874 - val_loss: 0.0277 - val_acc: 0.9913
Epoch 5/20

Epoch 00005: LearningRateScheduler setting learning rate to 0.0013181019.
60000/60000 [==============================] - 40s 664us/step - loss: 0.0335 - acc: 0.9898 - val_loss: 0.0314 - val_acc: 0.9889
Epoch 6/20

Epoch 00006: LearningRateScheduler setting learning rate to 0.0011560694.
60000/60000 [==============================] - 40s 661us/step - loss: 0.0305 - acc: 0.9904 - val_loss: 0.0278 - val_acc: 0.9912
Epoch 7/20

Epoch 00007: LearningRateScheduler setting learning rate to 0.0010295127.
60000/60000 [==============================] - 40s 661us/step - loss: 0.0282 - acc: 0.9910 - val_loss: 0.0242 - val_acc: 0.9909
Epoch 8/20

Epoch 00008: LearningRateScheduler setting learning rate to 0.0009279307.
60000/60000 [==============================] - 40s 661us/step - loss: 0.0258 - acc: 0.9918 - val_loss: 0.0197 - val_acc: 0.9936
Epoch 9/20

Epoch 00009: LearningRateScheduler setting learning rate to 0.0008445946.
60000/60000 [==============================] - 39s 657us/step - loss: 0.0246 - acc: 0.9918 - val_loss: 0.0216 - val_acc: 0.9934
Epoch 10/20

Epoch 00010: LearningRateScheduler setting learning rate to 0.0007749935.
60000/60000 [==============================] - 40s 659us/step - loss: 0.0231 - acc: 0.9924 - val_loss: 0.0218 - val_acc: 0.9925
Epoch 11/20

Epoch 00011: LearningRateScheduler setting learning rate to 0.0007159905.
60000/60000 [==============================] - 40s 668us/step - loss: 0.0207 - acc: 0.9928 - val_loss: 0.0175 - val_acc: 0.9940
Epoch 12/20

Epoch 00012: LearningRateScheduler setting learning rate to 0.000665336.
60000/60000 [==============================] - 39s 657us/step - loss: 0.0197 - acc: 0.9935 - val_loss: 0.0178 - val_acc: 0.9946
Epoch 13/20

Epoch 00013: LearningRateScheduler setting learning rate to 0.0006213753.
60000/60000 [==============================] - 40s 661us/step - loss: 0.0190 - acc: 0.9940 - val_loss: 0.0200 - val_acc: 0.9936
Epoch 14/20

Epoch 00014: LearningRateScheduler setting learning rate to 0.0005828638.
60000/60000 [==============================] - 40s 662us/step - loss: 0.0191 - acc: 0.9935 - val_loss: 0.0187 - val_acc: 0.9932
Epoch 15/20

Epoch 00015: LearningRateScheduler setting learning rate to 0.0005488474.
60000/60000 [==============================] - 40s 661us/step - loss: 0.0178 - acc: 0.9939 - val_loss: 0.0213 - val_acc: 0.9926
Epoch 16/20

Epoch 00016: LearningRateScheduler setting learning rate to 0.0005185825.
60000/60000 [==============================] - 40s 659us/step - loss: 0.0167 - acc: 0.9945 - val_loss: 0.0183 - val_acc: 0.9940
Epoch 17/20

Epoch 00017: LearningRateScheduler setting learning rate to 0.000491481.
60000/60000 [==============================] - 40s 660us/step - loss: 0.0167 - acc: 0.9944 - val_loss: 0.0176 - val_acc: 0.9940
Epoch 18/20

Epoch 00018: LearningRateScheduler setting learning rate to 0.0004670715.
60000/60000 [==============================] - 40s 664us/step - loss: 0.0161 - acc: 0.9946 - val_loss: 0.0174 - val_acc: 0.9941
Epoch 19/20

Epoch 00019: LearningRateScheduler setting learning rate to 0.0004449718.
60000/60000 [==============================] - 40s 663us/step - loss: 0.0153 - acc: 0.9949 - val_loss: 0.0192 - val_acc: 0.9936
Epoch 20/20

Epoch 00020: LearningRateScheduler setting learning rate to 0.000424869.
60000/60000 [==============================] - 40s 661us/step - loss: 0.0136 - acc: 0.9958 - val_loss: 0.0177 - val_acc: 0.9938

