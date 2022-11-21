# colab_SD_finetune_hack

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1DIS456XTho5d1Kf-ty_d23vVMBmcEFk_#scrollTo=uu2Dn3VP2mmE)

Prepare your dataset with huggingface's data prep library and upload to your huggingface repo. Then Simply change the two lines.
WARNING, No checkpoint save in between.

```
dataset_name="YOUR DATASET PATH"
  --output_dir="YOUR MODEL OUTPUT PATH"
```


```
MODEL_NAME="CompVis/stable-diffusion-v1-4"
dataset_name="treksis/again_test"

!accelerate launch /content/diffusers/examples/text_to_image/train_text_to_image.py \
  --pretrained_model_name_or_path=$MODEL_NAME \
  --dataset_name=$dataset_name \
  --use_ema \
  --resolution=512 --center_crop --random_flip \
  --train_batch_size=4 \
  --gradient_accumulation_steps=4 \
  --gradient_checkpointing \
  --mixed_precision="fp16" \
  --max_train_steps=10000 \
  --learning_rate=1e-05 \
  --max_grad_norm=1 \
  --lr_scheduler="constant" --lr_warmup_steps=0 \
  --output_dir="/content/gdrive/MyDrive/full-tuning"
```

Credit

https://github.com/TheLastBen/fast-stable-diffusion

https://github.com/LambdaLabsML/examples/tree/main/stable-diffusion-finetuning
