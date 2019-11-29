# Result of base model

Epoch 50/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3309 - acc: 0.8903 - val_loss: 0.5947 - val_acc: 0.8235

Model took 1015.01 seconds to train

weight_decay = 1e-4

# Define the model

model = Sequential()

model.add(SeparableConv2D(32, (3,3), kernel_regularizer=regularizers.l2(weight_decay), input_shape=(32,32,3))) #30X30 #3X3

model.add(Activation('relu'))

model.add(BatchNormalization())

model.add(SeparableConv2D(64, (3,3), kernel_regularizer=regularizers.l2(weight_decay))) #28X28 #5X5

model.add(Activation('relu'))

model.add(BatchNormalization())

model.add(SeparableConv2D(128, (3,3), kernel_regularizer=regularizers.l2(weight_decay)))#26X26 #7X7

model.add(Activation('relu'))

model.add(BatchNormalization())

model.add(MaxPooling2D(pool_size=(2,2)))#13X13 #8X8

model.add(Dropout(0.2))
 
model.add(SeparableConv2D(64, (1), kernel_regularizer=regularizers.l2(weight_decay))) #13X13 #8X8

model.add(Activation('relu'))

model.add(BatchNormalization())

model.add(SeparableConv2D(128, (3,3), kernel_regularizer=regularizers.l2(weight_decay))) #11X11 #12X12

model.add(Activation('relu'))

model.add(BatchNormalization())

model.add(SeparableConv2D(256, (3,3),kernel_regularizer=regularizers.l2(weight_decay))) #9X9 #16X16

model.add(Activation('relu'))

model.add(BatchNormalization())

model.add(MaxPooling2D(pool_size=(2,2))) #4X4 #18X18

model.add(Dropout(0.3))
 
model.add(SeparableConv2D(64, (1), kernel_regularizer=regularizers.l2(weight_decay))) #4X4 #18X18

model.add(Activation('relu'))

model.add(Flatten())

model.add(Dense(num_classes, activation='softmax'))

# Results
Epoch 1/50

Epoch 00001: LearningRateScheduler setting learning rate to 0.003.
390/390 [==============================] - 51s 130ms/step - loss: 1.4473 - acc: 0.4748 - val_loss: 2.0118 - val_acc: 0.4615
Epoch 2/50

Epoch 00002: LearningRateScheduler setting learning rate to 0.0022744503.
390/390 [==============================] - 45s 117ms/step - loss: 1.0897 - acc: 0.6133 - val_loss: 1.1878 - val_acc: 0.6099
Epoch 3/50

Epoch 00003: LearningRateScheduler setting learning rate to 0.0018315018.
390/390 [==============================] - 45s 116ms/step - loss: 0.9485 - acc: 0.6657 - val_loss: 1.0227 - val_acc: 0.6723
Epoch 4/50

Epoch 00004: LearningRateScheduler setting learning rate to 0.0015329586.
390/390 [==============================] - 45s 115ms/step - loss: 0.8710 - acc: 0.6924 - val_loss: 0.8286 - val_acc: 0.7213
Epoch 5/50

Epoch 00005: LearningRateScheduler setting learning rate to 0.0013181019.
390/390 [==============================] - 45s 115ms/step - loss: 0.8111 - acc: 0.7147 - val_loss: 0.8668 - val_acc: 0.7079
Epoch 6/50

Epoch 00006: LearningRateScheduler setting learning rate to 0.0011560694.
390/390 [==============================] - 45s 115ms/step - loss: 0.7675 - acc: 0.7306 - val_loss: 0.7482 - val_acc: 0.7430
Epoch 7/50

Epoch 00007: LearningRateScheduler setting learning rate to 0.0010295127.
390/390 [==============================] - 45s 115ms/step - loss: 0.7403 - acc: 0.7407 - val_loss: 0.7712 - val_acc: 0.7396
Epoch 8/50

Epoch 00008: LearningRateScheduler setting learning rate to 0.0009279307.
390/390 [==============================] - 45s 116ms/step - loss: 0.7077 - acc: 0.7515 - val_loss: 0.7436 - val_acc: 0.7559
Epoch 9/50

Epoch 00009: LearningRateScheduler setting learning rate to 0.0008445946.
390/390 [==============================] - 45s 115ms/step - loss: 0.6835 - acc: 0.7612 - val_loss: 0.6508 - val_acc: 0.7760
Epoch 10/50

Epoch 00010: LearningRateScheduler setting learning rate to 0.0007749935.
390/390 [==============================] - 45s 115ms/step - loss: 0.6745 - acc: 0.7621 - val_loss: 0.6700 - val_acc: 0.7702
Epoch 11/50

Epoch 00011: LearningRateScheduler setting learning rate to 0.0007159905.
390/390 [==============================] - 44s 114ms/step - loss: 0.6554 - acc: 0.7725 - val_loss: 0.6431 - val_acc: 0.7832
Epoch 12/50

Epoch 00012: LearningRateScheduler setting learning rate to 0.000665336.
390/390 [==============================] - 44s 114ms/step - loss: 0.6408 - acc: 0.7758 - val_loss: 0.6462 - val_acc: 0.7796
Epoch 13/50

Epoch 00013: LearningRateScheduler setting learning rate to 0.0006213753.
390/390 [==============================] - 45s 115ms/step - loss: 0.6288 - acc: 0.7813 - val_loss: 0.7052 - val_acc: 0.7682
Epoch 14/50

Epoch 00014: LearningRateScheduler setting learning rate to 0.0005828638.
390/390 [==============================] - 45s 115ms/step - loss: 0.6177 - acc: 0.7848 - val_loss: 0.6200 - val_acc: 0.7926
Epoch 15/50

Epoch 00015: LearningRateScheduler setting learning rate to 0.0005488474.
390/390 [==============================] - 45s 114ms/step - loss: 0.6068 - acc: 0.7898 - val_loss: 0.5912 - val_acc: 0.7994
Epoch 16/50

Epoch 00016: LearningRateScheduler setting learning rate to 0.0005185825.
390/390 [==============================] - 44s 114ms/step - loss: 0.5939 - acc: 0.7938 - val_loss: 0.5773 - val_acc: 0.8032
Epoch 17/50

Epoch 00017: LearningRateScheduler setting learning rate to 0.000491481.
390/390 [==============================] - 44s 113ms/step - loss: 0.5900 - acc: 0.7943 - val_loss: 0.5996 - val_acc: 0.7975
Epoch 18/50

Epoch 00018: LearningRateScheduler setting learning rate to 0.0004670715.
390/390 [==============================] - 44s 113ms/step - loss: 0.5859 - acc: 0.7944 - val_loss: 0.5889 - val_acc: 0.8009
Epoch 19/50

Epoch 00019: LearningRateScheduler setting learning rate to 0.0004449718.
390/390 [==============================] - 44s 113ms/step - loss: 0.5770 - acc: 0.7995 - val_loss: 0.6235 - val_acc: 0.7907
Epoch 20/50

Epoch 00020: LearningRateScheduler setting learning rate to 0.000424869.
390/390 [==============================] - 44s 113ms/step - loss: 0.5700 - acc: 0.7999 - val_loss: 0.6014 - val_acc: 0.7948
Epoch 21/50

Epoch 00021: LearningRateScheduler setting learning rate to 0.0004065041.
390/390 [==============================] - 44s 112ms/step - loss: 0.5597 - acc: 0.8038 - val_loss: 0.5821 - val_acc: 0.8008
Epoch 22/50

Epoch 00022: LearningRateScheduler setting learning rate to 0.000389661.
390/390 [==============================] - 44s 113ms/step - loss: 0.5542 - acc: 0.8082 - val_loss: 0.6183 - val_acc: 0.7921
Epoch 23/50

Epoch 00023: LearningRateScheduler setting learning rate to 0.0003741581.
390/390 [==============================] - 44s 113ms/step - loss: 0.5518 - acc: 0.8090 - val_loss: 0.6167 - val_acc: 0.7936
Epoch 24/50

Epoch 00024: LearningRateScheduler setting learning rate to 0.0003598417.
390/390 [==============================] - 45s 115ms/step - loss: 0.5491 - acc: 0.8089 - val_loss: 0.5774 - val_acc: 0.8047
Epoch 25/50

Epoch 00025: LearningRateScheduler setting learning rate to 0.0003465804.
390/390 [==============================] - 44s 114ms/step - loss: 0.5480 - acc: 0.8086 - val_loss: 0.5786 - val_acc: 0.8043
Epoch 26/50

Epoch 00026: LearningRateScheduler setting learning rate to 0.0003342618.
390/390 [==============================] - 45s 115ms/step - loss: 0.5380 - acc: 0.8135 - val_loss: 0.5730 - val_acc: 0.8052
Epoch 27/50

Epoch 00027: LearningRateScheduler setting learning rate to 0.0003227889.
390/390 [==============================] - 45s 115ms/step - loss: 0.5366 - acc: 0.8110 - val_loss: 0.5516 - val_acc: 0.8091
Epoch 28/50

Epoch 00028: LearningRateScheduler setting learning rate to 0.0003120774.
390/390 [==============================] - 46s 117ms/step - loss: 0.5280 - acc: 0.8139 - val_loss: 0.5863 - val_acc: 0.8009
Epoch 29/50

Epoch 00029: LearningRateScheduler setting learning rate to 0.000302054.
390/390 [==============================] - 45s 116ms/step - loss: 0.5308 - acc: 0.8136 - val_loss: 0.5625 - val_acc: 0.8088
Epoch 30/50

Epoch 00030: LearningRateScheduler setting learning rate to 0.0002926544.
390/390 [==============================] - 45s 116ms/step - loss: 0.5265 - acc: 0.8161 - val_loss: 0.5417 - val_acc: 0.8153
Epoch 31/50

Epoch 00031: LearningRateScheduler setting learning rate to 0.0002838221.
390/390 [==============================] - 46s 117ms/step - loss: 0.5219 - acc: 0.8177 - val_loss: 0.5488 - val_acc: 0.8151
Epoch 32/50

Epoch 00032: LearningRateScheduler setting learning rate to 0.0002755074.
390/390 [==============================] - 45s 116ms/step - loss: 0.5149 - acc: 0.8198 - val_loss: 0.5561 - val_acc: 0.8127
Epoch 33/50

Epoch 00033: LearningRateScheduler setting learning rate to 0.000267666.
390/390 [==============================] - 45s 116ms/step - loss: 0.5172 - acc: 0.8200 - val_loss: 0.5709 - val_acc: 0.8053
Epoch 34/50

Epoch 00034: LearningRateScheduler setting learning rate to 0.0002602585.
390/390 [==============================] - 45s 115ms/step - loss: 0.5133 - acc: 0.8213 - val_loss: 0.5499 - val_acc: 0.8162
Epoch 35/50

Epoch 00035: LearningRateScheduler setting learning rate to 0.00025325.
390/390 [==============================] - 45s 116ms/step - loss: 0.5150 - acc: 0.8193 - val_loss: 0.5324 - val_acc: 0.8188
Epoch 36/50

Epoch 00036: LearningRateScheduler setting learning rate to 0.0002466091.
390/390 [==============================] - 45s 114ms/step - loss: 0.5081 - acc: 0.8216 - val_loss: 0.5518 - val_acc: 0.8121
Epoch 37/50

Epoch 00037: LearningRateScheduler setting learning rate to 0.0002403076.
390/390 [==============================] - 45s 115ms/step - loss: 0.5065 - acc: 0.8228 - val_loss: 0.5384 - val_acc: 0.8209
Epoch 38/50

Epoch 00038: LearningRateScheduler setting learning rate to 0.0002343201.
390/390 [==============================] - 45s 115ms/step - loss: 0.5028 - acc: 0.8240 - val_loss: 0.5545 - val_acc: 0.8126
Epoch 39/50

Epoch 00039: LearningRateScheduler setting learning rate to 0.0002286237.
390/390 [==============================] - 45s 115ms/step - loss: 0.5019 - acc: 0.8252 - val_loss: 0.5357 - val_acc: 0.8167
Epoch 40/50

Epoch 00040: LearningRateScheduler setting learning rate to 0.0002231977.
390/390 [==============================] - 45s 115ms/step - loss: 0.4936 - acc: 0.8285 - val_loss: 0.5639 - val_acc: 0.8142
Epoch 41/50

Epoch 00041: LearningRateScheduler setting learning rate to 0.0002180233.
390/390 [==============================] - 45s 115ms/step - loss: 0.4991 - acc: 0.8253 - val_loss: 0.5477 - val_acc: 0.8173
Epoch 42/50

Epoch 00042: LearningRateScheduler setting learning rate to 0.0002130833.
390/390 [==============================] - 45s 116ms/step - loss: 0.4932 - acc: 0.8261 - val_loss: 0.5400 - val_acc: 0.8176
Epoch 43/50

Epoch 00043: LearningRateScheduler setting learning rate to 0.0002083623.
390/390 [==============================] - 45s 115ms/step - loss: 0.4939 - acc: 0.8282 - val_loss: 0.5326 - val_acc: 0.8220
Epoch 44/50

Epoch 00044: LearningRateScheduler setting learning rate to 0.0002038459.
390/390 [==============================] - 45s 115ms/step - loss: 0.4903 - acc: 0.8292 - val_loss: 0.5337 - val_acc: 0.8190
Epoch 45/50

Epoch 00045: LearningRateScheduler setting learning rate to 0.0001995211.
390/390 [==============================] - 45s 115ms/step - loss: 0.4890 - acc: 0.8290 - val_loss: 0.5412 - val_acc: 0.8197
Epoch 46/50

Epoch 00046: LearningRateScheduler setting learning rate to 0.0001953761.
390/390 [==============================] - 45s 115ms/step - loss: 0.4868 - acc: 0.8296 - val_loss: 0.5228 - val_acc: 0.8199
Epoch 47/50

Epoch 00047: LearningRateScheduler setting learning rate to 0.0001913998.
390/390 [==============================] - 45s 116ms/step - loss: 0.4871 - acc: 0.8295 - val_loss: 0.5501 - val_acc: 0.8166
Epoch 48/50

Epoch 00048: LearningRateScheduler setting learning rate to 0.0001875821.
390/390 [==============================] - 45s 115ms/step - loss: 0.4805 - acc: 0.8314 - val_loss: 0.5509 - val_acc: 0.8140
Epoch 49/50

Epoch 00049: LearningRateScheduler setting learning rate to 0.0001839137.
390/390 [==============================] - 45s 115ms/step - loss: 0.4878 - acc: 0.8312 - val_loss: 0.5333 - val_acc: 0.8207
Epoch 50/50

Epoch 00050: LearningRateScheduler setting learning rate to 0.000180386.
390/390 [==============================] - 45s 116ms/step - loss: 0.4810 - acc: 0.8321 - val_loss: 0.5334 - val_acc: 0.8199
Model took 2247.87 seconds to train
