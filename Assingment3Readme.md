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

# Define the model
model = Sequential()

model.add(SeparableConv2D(64, (3,3), kernel_regularizer=regularizers.l2(weight_decay), input_shape=(32,32,3))) #30 #3X3

model.add(Activation('relu'))

model.add(BatchNormalization())

model.add(Dropout(0.1))

model.add(SeparableConv2D(64, (3,3), kernel_regularizer=regularizers.l2(weight_decay))) #28 #5X5

model.add(Activation('relu'))

model.add(BatchNormalization())

model.add(Dropout(0.1))

model.add(SeparableConv2D(128, (3,3), kernel_regularizer=regularizers.l2(weight_decay)))#26 #7X7

model.add(Activation('relu'))

model.add(BatchNormalization())

model.add(MaxPooling2D(pool_size=(2,2)))#13 #8X8

model.add(Dropout(0.1))
 
model.add(SeparableConv2D(64, (1), kernel_regularizer=regularizers.l2(weight_decay))) #13 #8X8

model.add(Activation('relu'))

model.add(BatchNormalization())

model.add(Dropout(0.1))

model.add(SeparableConv2D(128, (3,3), kernel_regularizer=regularizers.l2(weight_decay))) #11 #12X12

model.add(Activation('relu'))

model.add(BatchNormalization())

model.add(Dropout(0.1))

model.add(SeparableConv2D(256, (3,3),kernel_regularizer=regularizers.l2(weight_decay))) #9 #16X16

model.add(Activation('relu'))

model.add(BatchNormalization())

model.add(Dropout(0.1))

model.add(MaxPooling2D(pool_size=(2,2))) #4 #18X18

model.add(Dropout(0.1))
 
model.add(SeparableConv2D(64, (1), kernel_regularizer=regularizers.l2(weight_decay))) #18X18

model.add(Activation('relu'))

model.add(SeparableConv2D(10, 1))

model.add(BatchNormalization())

model.add(Convolution2D(10, 4))

model.add(GlobalMaxPooling2D())

model.add(Activation('softmax'))

Total params: 87,255

Trainable params: 85,827

Non-trainable params: 1,428

# Results
Epoch 1/50

Epoch 00001: LearningRateScheduler setting learning rate to 0.005.
390/390 [==============================] - 56s 142ms/step - loss: 1.5320 - acc: 0.4364 - val_loss: 1.9440 - val_acc: 0.4551
Epoch 2/50

Epoch 00002: LearningRateScheduler setting learning rate to 0.0037907506.
390/390 [==============================] - 50s 129ms/step - loss: 1.2098 - acc: 0.5637 - val_loss: 1.2220 - val_acc: 0.5907
Epoch 3/50

Epoch 00003: LearningRateScheduler setting learning rate to 0.0030525031.
390/390 [==============================] - 51s 130ms/step - loss: 1.0583 - acc: 0.6226 - val_loss: 1.1488 - val_acc: 0.6047
Epoch 4/50

Epoch 00004: LearningRateScheduler setting learning rate to 0.002554931.
390/390 [==============================] - 51s 130ms/step - loss: 0.9628 - acc: 0.6580 - val_loss: 0.9109 - val_acc: 0.6869
Epoch 5/50

Epoch 00005: LearningRateScheduler setting learning rate to 0.0021968366.
390/390 [==============================] - 51s 130ms/step - loss: 0.8981 - acc: 0.6839 - val_loss: 0.9142 - val_acc: 0.6892
Epoch 6/50

Epoch 00006: LearningRateScheduler setting learning rate to 0.0019267823.
390/390 [==============================] - 51s 130ms/step - loss: 0.8419 - acc: 0.7021 - val_loss: 0.8253 - val_acc: 0.7168
Epoch 7/50

Epoch 00007: LearningRateScheduler setting learning rate to 0.0017158545.
390/390 [==============================] - 51s 130ms/step - loss: 0.7946 - acc: 0.7210 - val_loss: 0.8274 - val_acc: 0.7155
Epoch 8/50

Epoch 00008: LearningRateScheduler setting learning rate to 0.0015465512.
390/390 [==============================] - 50s 129ms/step - loss: 0.7669 - acc: 0.7300 - val_loss: 0.7231 - val_acc: 0.7529
Epoch 9/50

Epoch 00009: LearningRateScheduler setting learning rate to 0.0014076577.
390/390 [==============================] - 51s 130ms/step - loss: 0.7362 - acc: 0.7424 - val_loss: 0.7499 - val_acc: 0.7461
Epoch 10/50

Epoch 00010: LearningRateScheduler setting learning rate to 0.0012916559.
390/390 [==============================] - 51s 130ms/step - loss: 0.7122 - acc: 0.7498 - val_loss: 0.6534 - val_acc: 0.7758
Epoch 11/50

Epoch 00011: LearningRateScheduler setting learning rate to 0.0011933174.
390/390 [==============================] - 51s 130ms/step - loss: 0.6958 - acc: 0.7558 - val_loss: 0.6986 - val_acc: 0.7631
Epoch 12/50

Epoch 00012: LearningRateScheduler setting learning rate to 0.0011088933.
390/390 [==============================] - 51s 130ms/step - loss: 0.6772 - acc: 0.7622 - val_loss: 0.6774 - val_acc: 0.7697
Epoch 13/50

Epoch 00013: LearningRateScheduler setting learning rate to 0.0010356255.
390/390 [==============================] - 51s 130ms/step - loss: 0.6612 - acc: 0.7691 - val_loss: 0.6446 - val_acc: 0.7787
Epoch 14/50

Epoch 00014: LearningRateScheduler setting learning rate to 0.0009714397.
390/390 [==============================] - 51s 130ms/step - loss: 0.6460 - acc: 0.7736 - val_loss: 0.6522 - val_acc: 0.7721
Epoch 15/50

Epoch 00015: LearningRateScheduler setting learning rate to 0.0009147457.
390/390 [==============================] - 51s 130ms/step - loss: 0.6365 - acc: 0.7775 - val_loss: 0.6629 - val_acc: 0.7692
Epoch 16/50

Epoch 00016: LearningRateScheduler setting learning rate to 0.0008643042.
390/390 [==============================] - 50s 129ms/step - loss: 0.6283 - acc: 0.7795 - val_loss: 0.5985 - val_acc: 0.7969
Epoch 17/50

Epoch 00017: LearningRateScheduler setting learning rate to 0.000819135.
390/390 [==============================] - 50s 129ms/step - loss: 0.6185 - acc: 0.7846 - val_loss: 0.6150 - val_acc: 0.7888
Epoch 18/50

Epoch 00018: LearningRateScheduler setting learning rate to 0.0007784524.
390/390 [==============================] - 50s 129ms/step - loss: 0.6076 - acc: 0.7887 - val_loss: 0.6568 - val_acc: 0.7790
Epoch 19/50

Epoch 00019: LearningRateScheduler setting learning rate to 0.0007416197.
390/390 [==============================] - 50s 129ms/step - loss: 0.6035 - acc: 0.7888 - val_loss: 0.6086 - val_acc: 0.7924
Epoch 20/50

Epoch 00020: LearningRateScheduler setting learning rate to 0.000708115.
390/390 [==============================] - 50s 129ms/step - loss: 0.5941 - acc: 0.7926 - val_loss: 0.5922 - val_acc: 0.7999
Epoch 21/50

Epoch 00021: LearningRateScheduler setting learning rate to 0.0006775068.
390/390 [==============================] - 50s 129ms/step - loss: 0.5868 - acc: 0.7946 - val_loss: 0.6103 - val_acc: 0.7944
Epoch 22/50

Epoch 00022: LearningRateScheduler setting learning rate to 0.000649435.
390/390 [==============================] - 50s 129ms/step - loss: 0.5814 - acc: 0.7965 - val_loss: 0.5903 - val_acc: 0.8004
Epoch 23/50

Epoch 00023: LearningRateScheduler setting learning rate to 0.0006235969.
390/390 [==============================] - 50s 129ms/step - loss: 0.5711 - acc: 0.8013 - val_loss: 0.6158 - val_acc: 0.7957
Epoch 24/50

Epoch 00024: LearningRateScheduler setting learning rate to 0.0005997361.
390/390 [==============================] - 50s 129ms/step - loss: 0.5709 - acc: 0.8000 - val_loss: 0.5873 - val_acc: 0.8043
Epoch 25/50

Epoch 00025: LearningRateScheduler setting learning rate to 0.000577634.
390/390 [==============================] - 50s 129ms/step - loss: 0.5670 - acc: 0.8022 - val_loss: 0.5854 - val_acc: 0.8020
Epoch 26/50

Epoch 00026: LearningRateScheduler setting learning rate to 0.0005571031.
390/390 [==============================] - 50s 129ms/step - loss: 0.5624 - acc: 0.8037 - val_loss: 0.5955 - val_acc: 0.8029
Epoch 27/50

Epoch 00027: LearningRateScheduler setting learning rate to 0.0005379815.
390/390 [==============================] - 50s 129ms/step - loss: 0.5599 - acc: 0.8046 - val_loss: 0.5643 - val_acc: 0.8100
Epoch 28/50

Epoch 00028: LearningRateScheduler setting learning rate to 0.000520129.
390/390 [==============================] - 50s 129ms/step - loss: 0.5466 - acc: 0.8081 - val_loss: 0.6332 - val_acc: 0.7861
Epoch 29/50

Epoch 00029: LearningRateScheduler setting learning rate to 0.0005034233.
390/390 [==============================] - 50s 128ms/step - loss: 0.5471 - acc: 0.8082 - val_loss: 0.5384 - val_acc: 0.8173
Epoch 30/50

Epoch 00030: LearningRateScheduler setting learning rate to 0.0004877573.
390/390 [==============================] - 50s 129ms/step - loss: 0.5399 - acc: 0.8114 - val_loss: 0.5650 - val_acc: 0.8121
Epoch 31/50

Epoch 00031: LearningRateScheduler setting learning rate to 0.0004730369.
390/390 [==============================] - 50s 128ms/step - loss: 0.5346 - acc: 0.8129 - val_loss: 0.5623 - val_acc: 0.8118
Epoch 32/50

Epoch 00032: LearningRateScheduler setting learning rate to 0.000459179.
390/390 [==============================] - 50s 129ms/step - loss: 0.5337 - acc: 0.8125 - val_loss: 0.5653 - val_acc: 0.8088
Epoch 33/50

Epoch 00033: LearningRateScheduler setting learning rate to 0.0004461099.
390/390 [==============================] - 50s 129ms/step - loss: 0.5342 - acc: 0.8146 - val_loss: 0.5320 - val_acc: 0.8213
Epoch 34/50

Epoch 00034: LearningRateScheduler setting learning rate to 0.0004337642.
390/390 [==============================] - 50s 128ms/step - loss: 0.5289 - acc: 0.8152 - val_loss: 0.5771 - val_acc: 0.8102
Epoch 35/50

Epoch 00035: LearningRateScheduler setting learning rate to 0.0004220834.
390/390 [==============================] - 50s 129ms/step - loss: 0.5207 - acc: 0.8173 - val_loss: 0.5342 - val_acc: 0.8197
Epoch 36/50

Epoch 00036: LearningRateScheduler setting learning rate to 0.0004110152.
390/390 [==============================] - 50s 128ms/step - loss: 0.5250 - acc: 0.8162 - val_loss: 0.5227 - val_acc: 0.8243
Epoch 37/50

Epoch 00037: LearningRateScheduler setting learning rate to 0.0004005127.
390/390 [==============================] - 50s 129ms/step - loss: 0.5217 - acc: 0.8170 - val_loss: 0.5277 - val_acc: 0.8245
Epoch 38/50

Epoch 00038: LearningRateScheduler setting learning rate to 0.0003905335.
390/390 [==============================] - 52s 132ms/step - loss: 0.5179 - acc: 0.8202 - val_loss: 0.5287 - val_acc: 0.8260
Epoch 39/50

Epoch 00039: LearningRateScheduler setting learning rate to 0.0003810395.
390/390 [==============================] - 51s 130ms/step - loss: 0.5143 - acc: 0.8215 - val_loss: 0.5204 - val_acc: 0.8275
Epoch 40/50

Epoch 00040: LearningRateScheduler setting learning rate to 0.0003719961.
390/390 [==============================] - 51s 130ms/step - loss: 0.5121 - acc: 0.8212 - val_loss: 0.5327 - val_acc: 0.8212
Epoch 41/50

Epoch 00041: LearningRateScheduler setting learning rate to 0.0003633721.
390/390 [==============================] - 51s 130ms/step - loss: 0.5139 - acc: 0.8206 - val_loss: 0.5160 - val_acc: 0.8297
Epoch 42/50

Epoch 00042: LearningRateScheduler setting learning rate to 0.0003551389.
390/390 [==============================] - 51s 130ms/step - loss: 0.5059 - acc: 0.8225 - val_loss: 0.5070 - val_acc: 0.8306
Epoch 43/50

Epoch 00043: LearningRateScheduler setting learning rate to 0.0003472705.
390/390 [==============================] - 51s 130ms/step - loss: 0.5047 - acc: 0.8226 - val_loss: 0.5206 - val_acc: 0.8272
Epoch 44/50

Epoch 00044: LearningRateScheduler setting learning rate to 0.0003397432.
390/390 [==============================] - 51s 130ms/step - loss: 0.5054 - acc: 0.8231 - val_loss: 0.5147 - val_acc: 0.8263
Epoch 45/50

Epoch 00045: LearningRateScheduler setting learning rate to 0.0003325352.
390/390 [==============================] - 51s 130ms/step - loss: 0.5034 - acc: 0.8235 - val_loss: 0.5377 - val_acc: 0.8226
Epoch 46/50

Epoch 00046: LearningRateScheduler setting learning rate to 0.0003256268.
390/390 [==============================] - 51s 130ms/step - loss: 0.4982 - acc: 0.8260 - val_loss: 0.5242 - val_acc: 0.8256
Epoch 47/50

Epoch 00047: LearningRateScheduler setting learning rate to 0.0003189996.
390/390 [==============================] - 51s 130ms/step - loss: 0.5019 - acc: 0.8248 - val_loss: 0.5434 - val_acc: 0.8169
Epoch 48/50

Epoch 00048: LearningRateScheduler setting learning rate to 0.0003126368.
390/390 [==============================] - 51s 130ms/step - loss: 0.4948 - acc: 0.8290 - val_loss: 0.5256 - val_acc: 0.8239
Epoch 49/50

Epoch 00049: LearningRateScheduler setting learning rate to 0.0003065228.
390/390 [==============================] - 51s 130ms/step - loss: 0.4948 - acc: 0.8266 - val_loss: 0.5135 - val_acc: 0.8274
Epoch 50/50

Epoch 00050: LearningRateScheduler setting learning rate to 0.0003006434.
390/390 [==============================] - 50s 129ms/step - loss: 0.4923 - acc: 0.8296 - val_loss: 0.5139 - val_acc: 0.8261
Model2 took 2530.38 seconds to train
