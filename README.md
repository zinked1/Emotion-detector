# Emotion-detector
Detects happy, sad, and neutral


Cool Emotion Detector
Detects if you are happy, sad, or neutral

The Algorithm
Basically I used a classification AI and took 150 photos for each emotion to train it so it can easily tell peoples emotion based on the photo they give the AI.
Running this project







Get a Jetson nano and set it up with Visual studio Code

Then in the VS code terminal navigate to the classification data folder


Import the file called test I proved into the data file that is under classification. The file name is testdataset
        
Then in the vs code terminal, run these commands

First run the docker container: cd ~/jetson-inference/
./docker/run.sh




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

