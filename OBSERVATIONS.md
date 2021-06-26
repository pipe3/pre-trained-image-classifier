# Pre-trained Image Classifier
Observations from the project.

Author: Oliver Kuhles

Date: 26-Jun-2021

## Classify uploaded images

### General comments
I have used two private pictures of Dachshounds. Both were not recognized by any of the architectures. Therefore I have used a third picture which I downloaded from [Wikipedia](https://commons.wikimedia.org/wiki/File:DSC_0346_(10096362833).jpg) [^1] which shows a German shepherd dog. This picture was recognized as expected, so I continued with the observations accordingly.


[^1]: Picture from wikipedia licensed under the Creative Commons Attribution-Share Alike 2.0 Generic license. Picture used twice: as provided and horizontally mirrored

### Questions and answers

#### Q1
Q1 - Did the three model architectures classify the breed of dog in Dog_01.jpg to be the same breed? If not, report the differences in the classifications.

A1 - Yes, all architectures recognized the German shepherd correctly
- alexnet -- yes
- resnet -- yes
- vgg -- yes

Note: neither of the architectures recognized the Dachshounds correctly.
- alexnet: one recognized as a dog but wrong breed
 - Dachshund_01a.jpeg: Dog! Classifier: marmot
 - Dachshund_02a.jpeg: NotDog! Classifier: border terrier

- resnet: one recognized as a dog but wrong breed
 - Dachshund_01a.jpeg: NotDog! Classifier: marmot
 - Dachshund_02a.jpeg: Dog! Classifier: norfolk terrier

- vgg: both recognized as a dog but wrong breed
 - Dachshund_01a.jpeg: Dog! Classifier: airedale, airedale terrier
 - Dachshund_02a.jpeg: Dog! Classifier: irish wolfhound  


#### Q2
Q2 - Did each of the three model architectures classify the breed of dog in Dog_01.jpg to be the same breed of dog as that model architecture classified Dog_02.jpg? If not, report the differences in the classifications.

A2 -- None of the architectures classified the horizontal mirrored image correctly

Looking at the German shepherd:
- alexnet: German_shepherd_dog_01b.jpg:  Classifier: ox
- resnet: German_shepherd_dog_01b.jpg:  Classifier: sea lion
- vgg: German_shepherd_dog_01b.jpg:  Classifier: sea lion


Looking at the Dachshounds:
- alexnet: both Notdog!
 - Dachshund_01b.jpeg: Classifier: brown bear, bruin, ursus arctos
 - Dachshund_02b.jpeg: Classifier: wild boar, boar, sus scrofa

resnet: one recognized as dog but wrong breed
 - Dachshund_01b.jpeg: Classifier: border terrier
 - Dachshund_02b.jpeg: Classifier: warthog

vgg: one recognized as dog but wrong breed
 - Dachshund_01b.jpeg: Classifier: border terrier
 - Dachshund_02b.jpeg: Classifier: wild boar, boar, sus scrofa



#### Q3
Q3 - Did the three model architectures correctly classify Animal_Name_01.jpg and Object_Name_01.jpg to not be dogs? If not, report the misclassifications.

A3 animal - No, all architectures recognized the cat as a dog breed border collie

Note: tested with a picture of my cat Oskar, who has passed away but was the (cat)king of the road :)

- alexnet: file: Oskar_01.jpeg, pet label: oskar, classifier label: border collie
- resnet: file: Oskar_01.jpeg, pet label: oskar, classifier label: border collie
- vgg: file: Oskar_01.jpeg, pet label: oskar, classifier label: border collie

A3 object - Yes, all architectures recognized it as a NOTdog

Note: tested with a picture of a heating

alexnet: heizung   Classifier: pedestal, plinth, footstall   
resnet: heizung   Classifier: tripod
vgg: heizung   Classifier: tripod

#### Q4

Q4 - Based upon your answers for questions 1. - 3. above, select the model architecture that you feel did the best at classifying the four uploaded images. Describe why you selected that model architecture as the best on uploaded image classification.

A1 - I would choose vgg

vgg achieved the highest fit for identifying dogs correctly. While the architectures showed no real difference for the German shepherd, the difference becomes visible for the Dachshounds. Even though neither architecture classified the Dachshounds correctly, it is vgg which classified both as dogs. Even with the horizontally mirrored images, vgg was correct for one image.

However, if runtime or compute time is a criteria to use, then I would use resnet instead of vgg. It identified one of the Dachshounds correctly as dog and the elapsed time is significantly lower than for vgg.

Runtime evaluation:
- alexnet: ** Total Elapsed Runtime: 0:0:1
- resnet: ** Total Elapsed Runtime: 0:0:1
- vgg: ** Total Elapsed Runtime: 0:0:4


## Results tables

| Name     | Number     |
| :------------- | :------------- |
| Total images       | 8 |
| Dog images | 6 |
| Not-a-Dog images | 2 |


| CNN Model Architecture | % Not-a-Dog Correct | % Dogs Correct | % Breeds Correct | % Match Labels |
| - | - | - | - | - |
| AlexNet | 100.0% | 33.3 % | 16.6% | 12.5% |
| ResNet | 100.0% | 50.0% | 16.6% | 12.5% |
| VGG | 100.0% | 66.6% | 16.6% | 12.5% |
