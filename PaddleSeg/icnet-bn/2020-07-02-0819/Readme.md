训练指标如下:

|type|metrics|value|
|----|-------|-----|
|train|loss|0.007|
||acc|0.9959|
||mIoU|0.9883|
|val|acc|0.9126|
|| IoU|0.8095|

配置脚本如下:
```yaml
# 数据集配置
DATASET:
    DATA_DIR: "./dataset/mini_supervisely/"
    NUM_CLASSES: 2
    TEST_FILE_LIST: "./dataset/mini_supervisely/test.txt"
    TRAIN_FILE_LIST: "./dataset/mini_supervisely/train.txt"
    VAL_FILE_LIST: "./dataset/mini_supervisely/val.txt"
    VIS_FILE_LIST: "./dataset/mini_supervisely/test.txt"

# 预训练模型配置
MODEL:
    MODEL_NAME: "icnet"
    DEFAULT_NORM_TYPE: "bn"
    MULTI_LOSS_WEIGHT: "[1.0, 0.4, 0.16]"
    ICNET:
        DEPTH_MULTIPLIER: 0.5

# 其他配置
TRAIN_CROP_SIZE: (512, 512)
EVAL_CROP_SIZE: (512, 512)
AUG:
    AUG_METHOD: "unpadding"
    FIX_RESIZE_SIZE: (512, 512)
BATCH_SIZE: 4
TRAIN:
    PRETRAINED_MODEL_DIR: "./check/cp/"
    MODEL_SAVE_DIR: "./saved_model/icnet_optic/"
    SNAPSHOT_EPOCH: 50
TEST:
    TEST_MODEL: "./saved_model/icnet_optic/final"
SOLVER:
    NUM_EPOCHS: 1000
    LR: 0.0001
    LR_POLICY: "poly"
    OPTIMIZER: "adam"

```