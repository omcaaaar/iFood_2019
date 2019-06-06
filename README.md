# iFood_2019
This is a part of the fine-grained visual-categorization workshop ([FGVC6 workshop](https://sites.google.com/view/fgvc6/home)) at [CVPR 2019](http://cvpr2019.thecvf.com/).


**Description:**

![alt text](https://github.com/omcaaaar/iFood_2019/blob/master/food_banner.png)
What did you eat today? Wondering if you are eating a healthy diet? Automatic food identification can assist towards food intake monitoring to maintain a healthy diet. Food classification is a challenging problem due to the large number of food categories, high visual similarity between different food categories, as well as the lack of datasets that are large enough for training deep models. In this competition, we extend our last year's dataset to 251 fine-grained (prepared) food categories with 118,475 training images collected from the web. We provide human verified labels for both the validation set of 11,994 images and the test set of 28,377 images. The goal is to build a model to predict the fine-grained food-category label given an image.

The main challenges are:
  1. Fine-grained Classes: The classes are fine-grained and visually similar. For example, the dataset has 15 different types of cakes, and 10 different types of pastas.
  2. Noisy Data: Since the training images are crawled from the web, they often include images of raw ingredients or processed and packaged food items. This is referred to as cross-domain noise. Further, due to the fine-grained nature of food-categories, a training image may either be incorrectly labeled into a visually similar class or be annotated with with a single label despite having multiple food items.


**Evaluation:**

For each image <img src="https://rawgit.com/visipedia/inat_comp/master/svgs/77a3b857d53fb44e33b53e4c8b68351a.svg?invert_in_darkmode" align=middle width=5.642109pt height=21.60213pt/>, an algorithm will produce 3 labels <img src="https://rawgit.com/visipedia/inat_comp/master/svgs/655bedbaf4a65f397b5041d0fdecde4c.svg?invert_in_darkmode" align=middle width=15.601905pt height=22.74591pt/>, <img src="https://rawgit.com/visipedia/inat_comp/master/svgs/946e592e2b2753a9272767ae3dd5b9a9.svg?invert_in_darkmode" align=middle width=82.4274pt height=21.60213pt/>. For this competition each image has one ground truth label <img src="https://rawgit.com/visipedia/inat_comp/master/svgs/681a37b53b66acbc455e39ca3e6f1c41.svg?invert_in_darkmode" align=middle width=12.444795pt height=14.10255pt/>, and the error for that image is:
<p align="center"><img src="https://rawgit.com/visipedia/inat_comp/master/svgs/7a42826f81c53c77e0fef3c827238d25.svg?invert_in_darkmode" align=middle width=123.403665pt height=24.865665pt/></p>
Where
<p align="center"><img src="https://rawgit.com/visipedia/inat_comp/master/svgs/7a45c501d5042bd031a267f008fa2ae6.svg?invert_in_darkmode" align=middle width=190.2021pt height=49.13139pt/></p>

The overall error score for an algorithm is the average error over all <img src="https://rawgit.com/visipedia/inat_comp/master/svgs/f9c4988898e7f532b9f826a75014ed3c.svg?invert_in_darkmode" align=middle width=14.94405pt height=22.38192pt/> test images:
<p align="center"><img src="https://rawgit.com/visipedia/inat_comp/master/svgs/444adcac0c7cbb4a8419ee1484625349.svg?invert_in_darkmode" align=middle width=118.05123pt height=41.069655pt/></p>


**Submisstion file format:**

```
image_name,label1 label2 label3 
test_0001.jpg,0 1 10 
test_0002.jpg,1 3 5 
test_0003.jpg,0 5 1 
```

Please include the header as shown above for correct parsing. Each line will correspond to one test image and will be identified by the id (e.g test_0001.jpg refers to image test_0001.jpg) for computing accuracy.


**Data:**

There is a total of 251 food categories in the dataset. A complete list of classes is available [here](https://github.com/omcaaaar/iFood_2019/blob/master/data/class_list.txt).

Training data:

The training data consists of 118,475 images from 251 classes. The training data is collected from web images and consists of noisy labels.

Validation data:

The validation data consists of 11,994 images from 251 classes. The test data is collected from web images and the labels are human verified. It does not contain noisy labels.

Test data:

The test data consists of 28,377 images from 251 classes. The test data is collected from web images and the labels are human verified. It does not contain noisy labels.

Data download and format:

Data can be downloaded from the links below or from [Kaggle](https://www.kaggle.com/c/ifood-2019-fgvc6/overview).

[Annotations](https://food-x.s3.amazonaws.com/annot.tar) (3.0 MB)
* Running `md5sum annot.tar` on the tar file should produce 0c632c543ceed0e70f0eb2db58eda3ab
* The tar contains 4 files
     * class_list.txt: Contains the names of 251 class labels. This can be used to map class_ids with class names.
     * train_info.csv: Each line of this csv containing the "image_name,label" pair for training data. For example, "train_00000.jpg,94" refers to image train_00000.jpg having class_id 94. The class_id can be mapped to class name using class_list.txt.      
     * val_info.csv: Each line of this csv containing the "image_name,label" pair for validation data.
     * test_info.csv: csv only provides the list of test images.
 * We provide separate tars for train, val and test images as mentioned below.

[Train Images](https://food-x.s3.amazonaws.com/train.tar) (2.3 GB)
* Running `md5sum train.tar` on the tar file should produce 8e56440e365ee852dcb0953a9307e27f
* Contains training images.
* For label information see annotation file train_info.csv. 

[Validation Images](https://food-x.s3.amazonaws.com/val.tar) (231 MB)
* Running `md5sum val.tar` on the tar file should produce fa9a4c1eb929835a0fe68734f4868d3b
* Contains validation images.
* For label information see annotation file val_info.csv. 

[Test Images](https://food-x.s3.amazonaws.com/test.tar) (548 MB)
* Running `md5sum train.tar` on the tar file should produce 32479146dd081d38895e46bb93fed58f
* Contains testing images.
* The label will be evaluation on the evaluation server.

**Annotations:**

This folder contains some important files which we'll be using while training our models.

  1. [class_balance.csv](https://github.com/omcaaaar/iFood_2019/blob/master/annotaions/class_balance.csv) : Used to analyse class imbalance in the training data.
  
  2. [outliers.txt](https://github.com/omcaaaar/iFood_2019/blob/master/annotaions/outliers.txt) : Contains list of all noisy/misclassified images in the training data.
  
  3. [train_info_v2.csv](https://github.com/omcaaaar/iFood_2019/blob/master/annotaions/train_info_v2.csv), [val_info_v2,csv](https://github.com/omcaaaar/iFood_2019/blob/master/annotaions/val_info_v2.csv.csv) : Used to make data folders so that we can load the data using PyTorch's DataLoader before training starts.
  
  **Notebooks:**
  
  This folder contains all the notebook files we've used during this competition.
  
  We trained 4 networks seperately and ensembled them at the end. The typical training flow was to fine-tune a network which is pretrained on ImageNet for 15 epochs and then train a full network for 3-5 epochs. We used BCEWithLogitsLoss for this problem and optimizer was Adam with initial learning rate of 1e-4 and reducing it by the factor of 10 after certain steps using MultiStepLR scheduler, beta values were 0.9 and 0.999.
  
  The networks are : pnasnet, senet154, polynet and densenet201. The highest scoring model was polynet followed by senet154, pnasnet and densenet201 at last.
  
  We also tried cleaning dirty labels and then augmenting the data but unfortunately that didn't give promising results.
  
  The trained model files can be found [here](https://www.kaggle.com/ochaporkar/ifood-2019-models)
  
  **Results:**
  
    1. polynet : 86.26% (top-3 accuracy)
    2. senet154 : 85.76% (top-3 accuracy)
    3. pnasnet : 84.77% (top-3 accuracy)
    4. densenet201 : 81.20 (top-3 accuracy)
    
After ensembling these 4 networks we got 90.54% top-3 accuracy on the test data.

**Scope of improvement:**

Due to time constraint we could not try following techniques, but would have certainly helped us improving the accuracy by atleast 2-3%.

  1. mixup
  2. label smoothing
  3. DropBlock
  4. we also could have created food pretrained training data by selecting only food-related data in openImage, ImageNet Fall 2011 (inspired by the following paper: [Domain Adaptive Transfer Learning with Specialist Models](https://arxiv.org/abs/1811.07056))
  
  **References:**
  
    1. Competition link : [kaggle](https://www.kaggle.com/c/ifood-2019-fgvc6)
    2. Competition link : [github](https://github.com/karansikka1/iFood_2019)
    3. models : [pretrained-models](https://github.com/Cadene/pretrained-models.pytorch)
