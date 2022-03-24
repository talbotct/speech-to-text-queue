# Project 4 Queue System and Speech to Text

This is simple framework for running speech to text and queuing tasks with API calls such as these.  This will be slotted into my medical api and application project: https://github.com/talbotct/med-api-talbotct

Uses Google Cloud Speech API for speech to text: https://cloud.google.com/speech-to-text 

Uses Google Cloud Storage for holding .wav audio files: https://cloud.google.com/storage

Uses Rabbitmq and Pika for queues and sending tasks: https://www.rabbitmq.com/ https://pika.readthedocs.io/en/stable/

Can take .wav files from local directory or from Google Cloud Storage and convert them to text as an output.  Queue system uses a round robin setup to distribute tasks to receiving instances.  Can scale the "receiver.py" instances to any amount needed for use.  Each can take an extra task and hold it while completing its current task.  Other tasks are stored in the queue.


# Usage

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
