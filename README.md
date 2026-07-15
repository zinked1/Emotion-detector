# Emotion-detector
Detects happy, sad, and neutral

### The Algorithm
I used a classification AI and took 150 photos for each emotion to train my model so it can easily tell a persons emotion based on the photo they give the AI.


### Running this project
---

 1. Get a Jetson nano and set it up with Visual studio Code

 2. In the VS code terminal navigate to the classification/data folder

 3. Import the file called testdataset. I proved into the data file that is under classification. The file name is testdataset
        
Then in the vs code terminal, run these commands

First run the docker container: 

        cd ~/jetson-inference/
        ./docker/run.sh


hi

`hihihi`

Then navigate to the classification folder: cd python/training/classification


Then to train the model run the train.py script on the dataset: python3 train.py --model-dir=models/testdataset data/testdataset


Then we need to convert the pytorch model to ONNX: python3 onnx_export.py --model-dir=models/testdataset


Then save the current model paths
NET=models/testdataset
DATASET=data/testdataset




Finally this last script will load the AI model and test it. The last line of the script should be the photo you want to test.


imagenet.py \
  --model=$NET/resnet18.onnx \
  --labels=$DATASET/labels.txt \
  --input_blob=input_0 \
  --output_blob=output_0 \
  $DATASET/test/Happy/20260708-121802.jpg output.jpg

