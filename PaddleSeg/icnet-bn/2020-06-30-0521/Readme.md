训练指标如下:

|type|metrics|value|
|----|-------|-----|
|train|loss|0.0128|
||acc|0.99544|
||mIoU|0.98847|
|val|loss|0.8|
||acc|0.9226|
|| IoU|0.8304|

训练参数如下:

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
    SNAPSHOT_EPOCH: 5
TEST:
    TEST_MODEL: "./saved_model/icnet_optic/final"
SOLVER:
    NUM_EPOCHS: 500
    LR: 0.001
    LR_POLICY: "poly"
    OPTIMIZER: "adam"
```