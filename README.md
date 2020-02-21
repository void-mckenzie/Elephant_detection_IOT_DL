# Elephant_detection_IOT_DL

The aim of the project is to run an object detection model on Raspberry Pi to detect elephants from a camera feed. Once the elephant is detected, the image is uploaded to a cloud database. This is then retrieved by an android application automatically and an alert message is sent to the concerned authorities. Since the model is running on the Pi, there is no need to send the video to a server to process it. This greatly reduces latency, traffic and other network related bottlenecks.

For the webcam, you can either use a raspberry pi cam, or use your phone's live feed as the video input. This can be done by using the IPWebCam application. In the code file, just replace the IP Address with your phone's IPWebCam address. Both the Pi and the webcam-phone should be connected to the same network (for the Pi to access the live cam feed). 

(Note: 2 separate phones need to be used here since one will be acting as a web camera. We are working on extending the app into a sticky app to ensure that it can work in the background too)

The Tensorflow library needs to be built from source for the Raspberry Pi(for ARM processors) - Link: https://www.tensorflow.org/install/source_rpi

After the library has been built, copy the Code + SSD_MobileNet folder into the tensorflow/models/research/object_detection folder.

Initialize the IPWebCam in the first phone and run the code on Pi.

When the Detecto App (APK name is different from the App name) is opened, click the "Detect" button and the app will start to periodically check the database. This phone has no restrictions of being in the same network as that of the Pi and WebCam.

Once the image is detected, it is encoded and uploaded to the cloud DB from which the app can now retreive and display the image. Additionally, it will also send a message to the concerned authorities (since this is a prototype, the number was hardcoded).
