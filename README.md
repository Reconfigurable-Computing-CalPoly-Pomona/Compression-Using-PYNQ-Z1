# Compression-Using-PYNQ-Z1

### Overview


#### Team Members:

  1. Christine Duong: Electrical and Computer Engineering department, College of Engineering, California State Polytechnic University, Pomona.
  
  2. Michael Hicks: Electrical and Computer Engineering department, College of Engineering, California State Polytechnic University, Pomona.
  
  3. Edward Hwang: Electrical and Computer Engineering department, College of Engineering, California State Polytechnic University, Pomona.
  
  4. Cory Kim: Electrical and Computer Engineering department, College of Engineering, California State Polytechnic University, Pomona.
  
  5. Jaemin Kim: Electrical and Computer Engineering department, College of Engineering, California State Polytechnic University, Pomona.
  
  6. Ryan Toeung: Electrical and Computer Engineering department, College of Engineering, California State Polytechnic University, Pomona.

#### Supervising Professor:

**Mohamed El-Hadedy**: Assistant Professor, Electrical and Computer Engineering department, College of Engineering, California State Polytechnic University, Pomona.

**What is H.264 Video Compression**

Summary of H.264

Encoding –

When running through H.264 video compression, the video first must start out by running through an encoder. The encoder phase has three different states. Initially, the original video has to be passed into the encoder. The encoder would then run through a prediction process and then get transformed. Ultimately, after getting transformed, the encoder would then produce an encoded, compressed H.264 bitstream that would be allowed to be passed onto the decoder.

Decoding – 

The decoder is the second and final step when it comes to H.264 video compression. After the process of running through the encoder has been completed, the compressed video is ready for decoding. The decoder, similar to the encoder, also has three stages. First off, the compressed video bitstream has to be passed into the decoder. Once the decoder has received the bitstream, then an inverse transformation process will occur. Lastly, the video will then get reconstructed and then produce a compressed, H.264 video.

<p align="center">
<img src=https://github.com/Reconfigurable-Computing-CalPoly-Pomona/Compression-Using-PYNQ-Z1/blob/master/Source%20Code/Images/Flow.png>
														     
	Figure 1: Flow Chart for H.264
</p>

**Tutorial**

1. **To access the PYNQ files on board via USB:**
   - Open File Explorer
   - Type the following into the address bar
     - \\pynq\xilinx\openh264
     - Username : xilinx
     - Password : xilinx
     - This is the file directory that you can see the files that are on the PYNQ that we have built.
     - Note: These files can not be changed from here. Only modifiable through PuTTY.


2. **Changing the parameters for your video to be compressed (Simplest form).**
   - Files that need to be changed:
     - CmdLineExample.sh
       - This needs to have the proper file name within to run.
         - We use welsenc\_vd\_1d.cfg
     - The file welsenc\_vd\_1d.cfg
       - This needs to have the proper resolution in it.
       - This contains the videos FPS Maximum.
       - This contains the bitrate of the encode max and target.
       - This contains the name of the layer definition file used
         - We use layer2\_vd.cfg
     - The file layer2\_vd.cfg
       - Inside here you need to change
         - Resolution
         - FPS Output
   - Once these files are changed to the proper settings then you can proceed to the testing.

3. **To begin Testing**
   - Install and Open PUTTY
     - First Identify what port your PYNQ is plugged into on the PC
     - Place your COM# and the data rate to 115200
       - You can find your device port in your device manager if on windows
     - Make sure the board is powered on and then hit start on PuTTY
   - The board will boot in the PUTTY command prompt.
   - Change directory to the folder …/openh264/testbin
   - Inside the testbin folder you will find the script CmdLineExample.sh
     - This is the file that will run the test.
       - You can look inside and edit the files within here to run encoder and decoder.
       - Inside the files in this script that it is saying to run you can edit those to change many aspects of the encoder.
   - You can run the .sh files in PuTTY with the following commands:
     - sh filename.sh
     - ./filename.sh
   - After running the script, you will see a readout of the success of the encoder or decoder.

4. **Troubleshooting Errors**
   - Wrong Input File Type
     - Make sure that the video file is .YUV for this encoder.
   - Permission Denied
     - If you encounter permission denied, then you must follow a few steps to fix this. You need to assign permission to xilinx to read, write, and execute. To do this there are numerous ways to do this but the one we found was to assign read write and execute to the files that are referenced within the files being ran.
     - CmdLineExample.sh
       - The file inside the script
         - ../h263enc &quot;filename&quot;
     - Inside the &quot;filename&quot; file above the input and output file also needs permissions.
       - This is the .YUV being encoded
       - The .264 file it is writing bitstream to.
     - The best way to ensure that the file receives the permissions is the following command:
       - sudo chmod 777 &quot;filename&quot;
         - Be sure that you are in the directory of the file for this part.
     - Check the status of the permissions with:
       - ls -l (these are lowercase L)
       - you will see a string of letters -rwxrwxrwx that have the permissions of read write and execute on each file. Look up online if you are unsure of what the string means.
     - If this fails, then you can also change ownership of certain files to be xilinx to make the permissions easier to give.
