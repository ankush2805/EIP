# Result of base model

Epoch 50/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3309 - acc: 0.8903 - val_loss: 0.5947 - val_acc: 0.8235

Model took 1015.01 seconds to train

weight_decay = 1e-4

# Discuss

Initially started with no learning rate, and no dropout, saw problems, also read image augmentation,
Wish you could explain how to close model and discuss various last point strategies

# Define the model

weight_decay = 1e-4

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

model.add(SeparableConv2D(10, 1)) #4X4 #18X18

model.add(BatchNormalization())

model.add(Convolution2D(10, 4)) #4X4 #18X18

model.add(GlobalMaxPooling2D())

model.add(Activation('softmax'))

Total params: 84,663

Trainable params: 83,299

Non-trainable params: 1,364


# Results
Epoch 1/50

Epoch 00001: LearningRateScheduler setting learning rate to 0.005.
390/390 [==============================] - 51s 130ms/step - loss: 1.5113 - acc: 0.4525 - val_loss: 2.1221 - val_acc: 0.4740
Epoch 2/50

Epoch 00002: LearningRateScheduler setting learning rate to 0.0037907506.
390/390 [==============================] - 45s 114ms/step - loss: 1.1476 - acc: 0.5898 - val_loss: 1.2863 - val_acc: 0.5962
Epoch 3/50

Epoch 00003: LearningRateScheduler setting learning rate to 0.0030525031.
390/390 [==============================] - 45s 115ms/step - loss: 0.9956 - acc: 0.6489 - val_loss: 0.9848 - val_acc: 0.6707
Epoch 4/50

Epoch 00004: LearningRateScheduler setting learning rate to 0.002554931.
390/390 [==============================] - 45s 114ms/step - loss: 0.9001 - acc: 0.6822 - val_loss: 0.9261 - val_acc: 0.6829
Epoch 5/50

Epoch 00005: LearningRateScheduler setting learning rate to 0.0021968366.
390/390 [==============================] - 45s 114ms/step - loss: 0.8258 - acc: 0.7084 - val_loss: 0.8218 - val_acc: 0.7212
Epoch 6/50

Epoch 00006: LearningRateScheduler setting learning rate to 0.0019267823.
390/390 [==============================] - 45s 115ms/step - loss: 0.7776 - acc: 0.7270 - val_loss: 0.7491 - val_acc: 0.7406
Epoch 7/50

Epoch 00007: LearningRateScheduler setting learning rate to 0.0017158545.
390/390 [==============================] - 45s 115ms/step - loss: 0.7393 - acc: 0.7407 - val_loss: 0.7452 - val_acc: 0.7484
Epoch 8/50

Epoch 00008: LearningRateScheduler setting learning rate to 0.0015465512.
390/390 [==============================] - 44s 113ms/step - loss: 0.7053 - acc: 0.7538 - val_loss: 0.6811 - val_acc: 0.7700
Epoch 9/50

Epoch 00009: LearningRateScheduler setting learning rate to 0.0014076577.
390/390 [==============================] - 44s 114ms/step - loss: 0.6766 - acc: 0.7633 - val_loss: 0.7728 - val_acc: 0.7443
Epoch 10/50

Epoch 00010: LearningRateScheduler setting learning rate to 0.0012916559.
390/390 [==============================] - 45s 115ms/step - loss: 0.6546 - acc: 0.7731 - val_loss: 0.6577 - val_acc: 0.7739
Epoch 11/50

Epoch 00011: LearningRateScheduler setting learning rate to 0.0011933174.
390/390 [==============================] - 45s 114ms/step - loss: 0.6338 - acc: 0.7779 - val_loss: 0.6607 - val_acc: 0.7731
Epoch 12/50

Epoch 00012: LearningRateScheduler setting learning rate to 0.0011088933.
390/390 [==============================] - 44s 114ms/step - loss: 0.6142 - acc: 0.7864 - val_loss: 0.6442 - val_acc: 0.7834
Epoch 13/50

Epoch 00013: LearningRateScheduler setting learning rate to 0.0010356255.
390/390 [==============================] - 45s 114ms/step - loss: 0.5995 - acc: 0.7916 - val_loss: 0.6414 - val_acc: 0.7840
Epoch 14/50

Epoch 00014: LearningRateScheduler setting learning rate to 0.0009714397.
390/390 [==============================] - 44s 114ms/step - loss: 0.5925 - acc: 0.7942 - val_loss: 0.5864 - val_acc: 0.7976
Epoch 15/50

Epoch 00015: LearningRateScheduler setting learning rate to 0.0009147457.
390/390 [==============================] - 44s 114ms/step - loss: 0.5791 - acc: 0.8000 - val_loss: 0.6126 - val_acc: 0.7918
Epoch 16/50

Epoch 00016: LearningRateScheduler setting learning rate to 0.0008643042.
390/390 [==============================] - 44s 114ms/step - loss: 0.5678 - acc: 0.8043 - val_loss: 0.6082 - val_acc: 0.7931
Epoch 17/50

Epoch 00017: LearningRateScheduler setting learning rate to 0.000819135.
390/390 [==============================] - 44s 114ms/step - loss: 0.5520 - acc: 0.8086 - val_loss: 0.5658 - val_acc: 0.8067
Epoch 18/50

Epoch 00018: LearningRateScheduler setting learning rate to 0.0007784524.
390/390 [==============================] - 44s 113ms/step - loss: 0.5499 - acc: 0.8083 - val_loss: 0.6261 - val_acc: 0.7868
Epoch 19/50

Epoch 00019: LearningRateScheduler setting learning rate to 0.0007416197.
390/390 [==============================] - 44s 114ms/step - loss: 0.5386 - acc: 0.8122 - val_loss: 0.6399 - val_acc: 0.7886
Epoch 20/50

Epoch 00020: LearningRateScheduler setting learning rate to 0.000708115.
390/390 [==============================] - 44s 114ms/step - loss: 0.5307 - acc: 0.8142 - val_loss: 0.5612 - val_acc: 0.8112
Epoch 21/50

Epoch 00021: LearningRateScheduler setting learning rate to 0.0006775068.
390/390 [==============================] - 44s 114ms/step - loss: 0.5228 - acc: 0.8174 - val_loss: 0.5597 - val_acc: 0.8076
Epoch 22/50

Epoch 00022: LearningRateScheduler setting learning rate to 0.000649435.
390/390 [==============================] - 44s 113ms/step - loss: 0.5230 - acc: 0.8167 - val_loss: 0.6015 - val_acc: 0.8008
Epoch 23/50

Epoch 00023: LearningRateScheduler setting learning rate to 0.0006235969.
390/390 [==============================] - 44s 113ms/step - loss: 0.5143 - acc: 0.8206 - val_loss: 0.5499 - val_acc: 0.8135
Epoch 24/50

Epoch 00024: LearningRateScheduler setting learning rate to 0.0005997361.
390/390 [==============================] - 44s 113ms/step - loss: 0.5104 - acc: 0.8223 - val_loss: 0.5488 - val_acc: 0.8146
Epoch 25/50

Epoch 00025: LearningRateScheduler setting learning rate to 0.000577634.
390/390 [==============================] - 44s 114ms/step - loss: 0.5048 - acc: 0.8244 - val_loss: 0.5904 - val_acc: 0.8013
Epoch 26/50

Epoch 00026: LearningRateScheduler setting learning rate to 0.0005571031.
390/390 [==============================] - 44s 113ms/step - loss: 0.5016 - acc: 0.8260 - val_loss: 0.5753 - val_acc: 0.8076
Epoch 27/50

Epoch 00027: LearningRateScheduler setting learning rate to 0.0005379815.
390/390 [==============================] - 44s 113ms/step - loss: 0.4882 - acc: 0.8307 - val_loss: 0.5889 - val_acc: 0.8021
Epoch 28/50

Epoch 00028: LearningRateScheduler setting learning rate to 0.000520129.
390/390 [==============================] - 44s 114ms/step - loss: 0.4918 - acc: 0.8288 - val_loss: 0.5706 - val_acc: 0.8071
Epoch 29/50

Epoch 00029: LearningRateScheduler setting learning rate to 0.0005034233.
390/390 [==============================] - 44s 112ms/step - loss: 0.4854 - acc: 0.8326 - val_loss: 0.5225 - val_acc: 0.8233
Epoch 30/50

Epoch 00030: LearningRateScheduler setting learning rate to 0.0004877573.
390/390 [==============================] - 44s 113ms/step - loss: 0.4857 - acc: 0.8320 - val_loss: 0.5389 - val_acc: 0.8167
Epoch 31/50

Epoch 00031: LearningRateScheduler setting learning rate to 0.0004730369.
390/390 [==============================] - 44s 114ms/step - loss: 0.4811 - acc: 0.8338 - val_loss: 0.5715 - val_acc: 0.8078
Epoch 32/50

Epoch 00032: LearningRateScheduler setting learning rate to 0.000459179.
390/390 [==============================] - 44s 113ms/step - loss: 0.4811 - acc: 0.8325 - val_loss: 0.5393 - val_acc: 0.8135
Epoch 33/50

Epoch 00033: LearningRateScheduler setting learning rate to 0.0004461099.
390/390 [==============================] - 44s 113ms/step - loss: 0.4698 - acc: 0.8364 - val_loss: 0.5282 - val_acc: 0.8190
Epoch 34/50

Epoch 00034: LearningRateScheduler setting learning rate to 0.0004337642.
390/390 [==============================] - 44s 113ms/step - loss: 0.4693 - acc: 0.8376 - val_loss: 0.5113 - val_acc: 0.8268
Epoch 35/50

Epoch 00035: LearningRateScheduler setting learning rate to 0.0004220834.
390/390 [==============================] - 44s 113ms/step - loss: 0.4702 - acc: 0.8362 - val_loss: 0.5180 - val_acc: 0.8227
Epoch 36/50

Epoch 00036: LearningRateScheduler setting learning rate to 0.0004110152.
390/390 [==============================] - 44s 113ms/step - loss: 0.4586 - acc: 0.8407 - val_loss: 0.5283 - val_acc: 0.8179
Epoch 37/50

Epoch 00037: LearningRateScheduler setting learning rate to 0.0004005127.
390/390 [==============================] - 44s 112ms/step - loss: 0.4641 - acc: 0.8375 - val_loss: 0.5275 - val_acc: 0.8223
Epoch 38/50

Epoch 00038: LearningRateScheduler setting learning rate to 0.0003905335.
390/390 [==============================] - 44s 112ms/step - loss: 0.4680 - acc: 0.8379 - val_loss: 0.5175 - val_acc: 0.8215
Epoch 39/50

Epoch 00039: LearningRateScheduler setting learning rate to 0.0003810395.
390/390 [==============================] - 44s 112ms/step - loss: 0.4505 - acc: 0.8434 - val_loss: 0.5317 - val_acc: 0.8170
Epoch 40/50

Epoch 00040: LearningRateScheduler setting learning rate to 0.0003719961.
390/390 [==============================] - 44s 112ms/step - loss: 0.4504 - acc: 0.8430 - val_loss: 0.5315 - val_acc: 0.8193
Epoch 41/50

Epoch 00041: LearningRateScheduler setting learning rate to 0.0003633721.
390/390 [==============================] - 44s 112ms/step - loss: 0.4499 - acc: 0.8445 - val_loss: 0.4989 - val_acc: 0.8285
Epoch 42/50

Epoch 00042: LearningRateScheduler setting learning rate to 0.0003551389.
390/390 [==============================] - 44s 112ms/step - loss: 0.4469 - acc: 0.8435 - val_loss: 0.5015 - val_acc: 0.8290
Epoch 43/50

Epoch 00043: LearningRateScheduler setting learning rate to 0.0003472705.
390/390 [==============================] - 44s 112ms/step - loss: 0.4509 - acc: 0.8399 - val_loss: 0.5105 - val_acc: 0.8275
Epoch 44/50

Epoch 00044: LearningRateScheduler setting learning rate to 0.0003397432.
390/390 [==============================] - 44s 112ms/step - loss: 0.4405 - acc: 0.8471 - val_loss: 0.5181 - val_acc: 0.8234
Epoch 45/50

Epoch 00045: LearningRateScheduler setting learning rate to 0.0003325352.
390/390 [==============================] - 44s 112ms/step - loss: 0.4462 - acc: 0.8450 - val_loss: 0.5082 - val_acc: 0.8287
Epoch 46/50

Epoch 00046: LearningRateScheduler setting learning rate to 0.0003256268.
390/390 [==============================] - 44s 112ms/step - loss: 0.4455 - acc: 0.8438 - val_loss: 0.5008 - val_acc: 0.8295
Epoch 47/50

Epoch 00047: LearningRateScheduler setting learning rate to 0.0003189996.
390/390 [==============================] - 44s 112ms/step - loss: 0.4417 - acc: 0.8457 - val_loss: 0.5162 - val_acc: 0.8262
Epoch 48/50

Epoch 00048: LearningRateScheduler setting learning rate to 0.0003126368.
390/390 [==============================] - 44s 112ms/step - loss: 0.4374 - acc: 0.8470 - val_loss: 0.5091 - val_acc: 0.8261
Epoch 49/50

Epoch 00049: LearningRateScheduler setting learning rate to 0.0003065228.
390/390 [==============================] - 44s 112ms/step - loss: 0.4363 - acc: 0.8475 - val_loss: 0.5001 - val_acc: 0.8299
Epoch 50/50

Epoch 00050: LearningRateScheduler setting learning rate to 0.0003006434.
390/390 [==============================] - 44s 112ms/step - loss: 0.4310 - acc: 0.8493 - val_loss: 0.5129 - val_acc: 0.8283
Model2 took 2214.81 seconds to train
