# EVA

# EVA S8 notes:

## Building the architecture of Resnet - 18
1) A basic  resnet architectue is built using the concepts of Resnet 18 as available in the documentation. The same is shown below.<br>
2) This architecture of resnet has been modified by passing it through a custsom built class to break down the network to extract the convolution at the level of 8x8 channel output, which is at the 3th block. This is preferred so that the heat map superimposition may be significantly big enough to understand the learning of the model. <br>
![resnet breakdown](https://user-images.githubusercontent.com/48343095/125080935-0b7ef600-e0e3-11eb-9147-f81eacf1262a.png) <br>
3) A backward hook is incorporated at the fourth block layer. The rest of the network is the same. Max pooling layer has been applied before the classification layer to accomodate for the dimensions of the image. <br>
![gradient](https://user-images.githubusercontent.com/48343095/125083112-9d87fe00-e0e5-11eb-803b-e60ab52e1cf9.png) <br>
4) The following are the modifications of the network. <br>
- Layer normalization at every layer of the architecture <br>
![layernormalization](https://user-images.githubusercontent.com/48343095/125080212-2d2bad80-e0e2-11eb-8243-3116f580f322.png) <br>
- Incoproration of Reduce Learning rate on Plateau which is implemented at the end of every epoch. <br>
-![reducelr1](https://user-images.githubusercontent.com/48343095/125080250-39b00600-e0e2-11eb-9ce0-967c8dd30d46.PNG) ![reducelr2](https://user-images.githubusercontent.com/48343095/125080267-3f0d5080-e0e2-11eb-94fa-697f80e476c1.PNG) <br>
- Incorporation of augmemntation techinques such as rotate(+/-5), Cutout (16x16), and random crop of the images. <br>
![augmentations](https://user-images.githubusercontent.com/48343095/125080300-4af91280-e0e2-11eb-9384-84a526d3b09f.PNG) <br>

5) Training is done for 40 epochs. <br>
![epochs 40](https://user-images.githubusercontent.com/48343095/125094222-b4801d80-e0f0-11eb-94e6-c23752284707.PNG)<br>
6) The training and validation losses/accuracy for 40 epochs is as shown below <br>
![losses graph](https://user-images.githubusercontent.com/48343095/125094266-bea21c00-e0f0-11eb-96fa-7ca91064f021.PNG) <br>
6) The misclasified images are plotted using a custom class built and the heat map of the grad cam is plotted againt the images. The heat map shows which part of the image the model has identified to miclassify the image. Since the images are of low definition the clarity of the grad cam may not be well established and explained. However the same may be utilized to classify higher quality images. <br>
![grad1](https://user-images.githubusercontent.com/48343095/125094690-1771b480-e0f1-11eb-936f-dfb4fe5b39f7.PNG)
![grad2](https://user-images.githubusercontent.com/48343095/125094700-193b7800-e0f1-11eb-97ea-8b106879e5db.PNG)
![grad3](https://user-images.githubusercontent.com/48343095/125094705-19d40e80-e0f1-11eb-908b-c203a57c6f58.PNG)
![grad4](https://user-images.githubusercontent.com/48343095/125094709-19d40e80-e0f1-11eb-8c48-2b2e07cfe3ee.PNG)
![grad5](https://user-images.githubusercontent.com/48343095/125094765-23f60d00-e0f1-11eb-8223-a1243278db5d.PNG)


7) The amount of gradient in the heat cam to be applied or super imposed on the original image may be varied by using a hyperpara

