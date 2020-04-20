# Deploy a People Counter App at the Edge

For this project, I used [SSD MobileNet V2 COCO model](http://download.tensorflow.org/models/object_detection/ssd_mobilenet_v2_coco_2018_03_29.tar.gz) and converted it to an Intermediate Representation for use with the Model Optimizer. Utilizing the Inference Engine, I used the model to perform inference on an input video, and extract useful data concerning the count of people in frame and how long they stay in frame. I sent this information as well as the output frame over MQTT, in order to view it from a separate UI server over a network.

## Downloading the Model
- First, in the terminal, type ***wget http://download.tensorflow.org/models/object_detection/ssd_mobilenet_v2_coco_2018_03_29.tar.gz**
- Then switched to the model directory using  
## Running the App

First, get the MQTT broker and UI installed.

- cd webservice/server
- npm install
- When complete, cd ../ui
- And again, npm install

You will need four separate terminal windows open in order to see the results. The steps below should be done in a different terminal based on number.

1. Get the MQTT broker installed and running.
- cd webservice/server/node-server
- node ./server.js
- You should see a message that Mosca server started.

2. Get the UI Node Server running.
- cd webservice/ui
- npm run dev
- After a few seconds, you should see webpack: Compiled successfully.

3. Start the ffserver
- sudo ffserver -f ./ffmpeg/server.conf

4. Running the App
- If using Udacity's Workspace, don't forget to click the SOURCE button.
- python main.py -i resources/Pedestrian_Detect_2_1_1.mp4 -m /home/workspace/models/frozen_inference_graph.xml -l /opt/intel/openvino/deployment_tools/inference_engine/lib/intel64/libcpu_extension_sse4.so -d CPU -pt 0.6 | ffmpeg -v warning -f rawvideo -pixel_format bgr24 -video_size 768x432 -framerate 24 -i - http://0.0.0.0:3004/fac.ffm

Result:

<video src="sample_output/output.mp4" width=500px height=500px></video>
