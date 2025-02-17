## Project overview 

1. receive low-resolution medical images provided by the user and train them through GAN (using checkpoints) 
2. improve resolution via the GAN's Generator  
3. provide users with improved images

- When a user provides image data to Server 1, Server 1 requests weight training information from another server, Server 2, which uses a GAN model. Server 2 trains on the
  appropriate dataset with GAN, stores the weights, and Server 1 uses the weight file to improve the image and serve it to the user.
- mageUploader is the relationship that provides data to ImageResizer and ImagePreviewer. GanServerInterface is the relationship that manages GanModel and WeightManager.
  ImageEnhancer receives weights from WeightManager and performs the function of enhancing the image. ImageDownloader, ComparisonTool, and PerformanceEvaluator are relationships
  that consume the output generated by ImageEnhancer. 
- To elaborate on these relationships, ImageUploader has a one-to-many relationship with multiple ImageResizers and ImagePreviewers, and GanServerInterface has a one-to-many
  relationship with GanModel and WeightManager. ImageEnhancer has a many-to-one relationship with WeightManager, which receives its weight from WeightManager, and ImageDownloader,
  ComparisonTool, and PerformanceEvaluator each form a one-to-one relationship with ImageEnhancer.
- The ImageUploader provides data to the ImageResizer and ImagePreviewer. It is used to resize images and generate previews after they are uploaded. GanServerInterface manages
  GanModel and WeightManager. This relationship is responsible for training the model and managing the weights throughout. ImageEnhancer gets weight information from WeightManager
  to enhance images. ImageDownloader, ComparisonTool, and PerformanceEvaluator all use image data generated by ImageEnhancer. 

<img src="./images/Before : After Brain Tumor MRI Enhancement.png" high="600px" width="600px"></img>

MRI of brain tumors improved using GANs 

## 'A Parallelism-Based, Stepwise Approach to GAN for Efficient Stability Training' 

<img src="./images/A Parallelism-Based, Stepwise Approach to GAN for Efficient Stability Training.png" width="400px"></img>

## PSTGAN

<img src="./images/Progressive Step Learning_Generator.png" width="400px"></img>
<img src="./images/Progressive Step Learning_Discriminator.tiff" width="400px"></img>

<img src="./images/Linear Mixing for Weighting on a Model-by-Model Basis .png" width="400px"></img>


	Developing a weight transfer mechanism to utilize previous model weights.

	Implementing a model training loop with hyperparameter adjustments based on the learning rate.


## SRGAN
Implementation of _Photo-Realistic Single Image Super-Resolution Using a Generative Adversarial Network_.

[Code](srgan/srgan.py)

Paper: https://arxiv.org/abs/1609.04802

<p align="center">
    <img src="http://eriklindernoren.se/images/superresgan.png" width="640"\>
</p>


## Example
```
$ cd srgan/
<follow steps at the top of srgan.py>
$ python3 srgan.py
```

<p align="center">
    <img src="http://eriklindernoren.se/images/srgan.png" width="640"\>
</p>

## Use_Start the serve

One command

```bash
$ python manage.py runserver
```

## Results screen 
#### Main page
<img src="./images/Main page .png" width="400px"></img>

#### Select Options page 
<img src="./images/Select Options page .png" width="400px"></img>

#### Result 
<img src="./images/Result .png" width="400px"></img>
