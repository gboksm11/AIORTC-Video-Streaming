Video and Data Channel Server
====================================

This example illustrates establishing a video and a data channel with a
browser. The browser (client-side) has access to a camera and sends video feed
to the python server via WebRTC. Server-side, the video feed is processed and is
fed into yolov5 every ~1 sec, where objects in the feed are detected and relayed
back to the client. In addition, the video feed is relayed back to the client.

Running
-------

First install the required packages:

.. code-block:: console

    $ pip install -r requirements.txt
    
    
Note: There might be additional dependencies not covered in the requirements.txt.

When you start the example, it will create an HTTP server which you
can connect to from your browser:

.. code-block:: console

    $ python server.py

You can then browse to the following page with your browser:

http://127.0.0.1:8080 (if browsing on same machine)

To browse the page on a different machine, you will need to download `[ngrok](https://ngrok.com/download)`
You should use ngrok to 1. make your server secure (served via Https) so that your client works, and 
2. to serve your server over the network. Once you have ngrok downloaded, first run your server on your machine,
then open the ngrok executable and run `ngrok http 8080` to create a tunnel serving your server at port 8080. 
Open the generated link on another machine, you can now see the served html. Make sure you check "use stun servers"
if you're accessing the files over the network.

Once you click `Start` the browser will send the video from its
webcam to the server.

The server will send the received video back to the browser, along with object recognition output.

Additional options
------------------

If you want to enable verbose logging, run:

.. code-block:: console

    $ python server.py -v
