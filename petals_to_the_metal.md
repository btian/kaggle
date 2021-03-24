# Petals to the Metal

https://www.kaggle.com/c/tpu-getting-started/overview

This competition shows how to train a computer vision model using TPUs.

The notebook is based on [this tutorial](https://www.kaggle.com/ryanholbrook/create-your-first-submission).
I got a score of 0.04203 from the first submission, which is not very good.
I did the following modifications to bring my score to the state of the art, ~0.97.

### Use a modern neural network

Instead of VGG16, I used EfficientNetB0 (I chose B0 because it's the fastest to train,
which allows me to iterate quickly). I didn't freeze the buttom layers, which lets them
be fine-tuned during the training process. The score increased to 0.887, which is a huge
jump.

Next, I applied more advanced data augmentation (shift, shear, rotate, random blockout) to
prevent overfitting. That brought up the submission score to just over 0.9.

Then I added more data to the training dataset by using the `tf-flower-photo-tfrec` dataset.
Score increased to 0.95791.

Finally, I used a 512x512 images instead of 224x224, and used a larger model, EfficientNetB6
to get my final score of 0.96892.