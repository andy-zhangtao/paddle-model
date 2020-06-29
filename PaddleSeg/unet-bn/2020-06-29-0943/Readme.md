[点击此处查看脚本内容](./597911.md)

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
    MODEL_NAME: "unet"
    DEFAULT_NORM_TYPE: "bn"

# 其他配置
TRAIN_CROP_SIZE: (512, 512)
EVAL_CROP_SIZE: (512, 512)
AUG:
    AUG_METHOD: "unpadding"
    FIX_RESIZE_SIZE: (512, 512)
BATCH_SIZE: 4
TRAIN:
    PRETRAINED_MODEL_DIR: "./check/final/"
    MODEL_SAVE_DIR: "./saved_model/unet_optic/"
    SNAPSHOT_EPOCH: 50
TEST:
    TEST_MODEL: "./saved_model/unet_optic/final"
SOLVER:
    NUM_EPOCHS: 100
    LR: 0.0001
    LR_POLICY: "poly"
    OPTIMIZER: "adam"
```

