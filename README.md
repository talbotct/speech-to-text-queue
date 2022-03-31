# EC530 Project 4 Queue System and Speech to Text

This is simple framework for running speech to text and queuing tasks with API calls such as these.  This will be slotted into my medical api and application project: https://github.com/talbotct/med-api-talbotct

Uses Google Cloud Speech API for speech to text: https://cloud.google.com/speech-to-text 

Uses Google Cloud Storage for holding .wav audio files: https://cloud.google.com/storage

Uses Rabbitmq and Pika for queues and sending tasks: https://www.rabbitmq.com/ https://pika.readthedocs.io/en/stable/

Can take .wav files from local directory or from Google Cloud Storage and convert them to text as an output.  Queue system uses a round robin setup to distribute tasks to receiving instances.  Can scale the "receiver.py" instances to any amount needed for use.  Each can take an extra task and hold it while completing its current task.  Other tasks are stored in the queue.  Rabbitmq based on tutorials on Rabbitmq website and speech to text based on https://www.youtube.com/watch?v=lKra6E_tp5U&ab_channel=JieJenn

Originally had my access key in the repo because I thought it was private but I realized it wasn't, this was an issue.  This json is needed to use the API.  I can provide if needed, the Prof. said photos of my results should suffice.  If you need to test the cloud storage links I can provide access.


# Usage

Install Erlang: https://www.erlang.org/downloads

Set Erlang PATH variable: 

Example:

![036deaa3e127d6d8e00be0b993a23ca3](https://user-images.githubusercontent.com/56003386/160987027-590ccdbe-887b-402d-8ca4-48ef4ace8256.png)

Install RabbitMQ: https://www.rabbitmq.com/download.html

Navigate to server sbin folder of RabbitMQ location.  This should be found within the erlang install location.

cd "C:\Program Files\erl-24.3.2\lib\rabbitmq-server-windows-3.9.13\rabbitmq_server-3.9.13\sbin"

Run .\rabbitmq-server.bat 

For to launch the server on a local host.  Can visit http://localhost:15672/ in your browser to monitor activity.

Run as many receiver.py instances as you would like to support on RabbitMQ.  

Then run producer.py with the .wav filename or Google cloud storage link (gs:) in command line.  e.g. (gs://ttaylor-speech-to-text/testSpeech2.wav)

# Photos of Usage

Data Storage of audio files for cloud testing:

![840df1778d8ca3790926d8bfa0b18477](https://user-images.githubusercontent.com/56003386/159937767-523447d0-fbc3-48cf-9e04-6f7b94702d9e.png)

Sending multiple tasks to the queue:

![4f0d9868c8dc925d09b130e4f26a1f50](https://user-images.githubusercontent.com/56003386/159937612-fab1380f-ab4b-455f-9f67-538e3fb44cba.png)

Output of call to Speech to Text api and my function:

![1e85cd086fa989562604368498c83747](https://user-images.githubusercontent.com/56003386/159937324-1714e4dd-6fb0-4c71-9202-2cde110d9124.png)

Rabbitmq manager showing sent tasks:

![b254a7662c51b40c6d979062a5d15eb5](https://user-images.githubusercontent.com/56003386/159938308-eb1ecd5a-80cb-4a35-9245-a789d8ba8f97.png)
