# Problem 1
## Introduction:
Given is a Wireshark Capture File that has been captured in a coffee shop.
## Tools Used: 
Wireshark, Google (research about Wireshark & exporting a HTTP object from Wireshark)
## Analysis:

<p align="center" width="100%">
    <img src="https://github.com/JothishKamal/task-7-cybersec/blob/main/images/PurpleBlock.png?raw=true">
</p>

In this screenshot (packets 6,8,10,12), we can clearly see that the user in logging into a ftp server with the following credentials:  
USER=0ffs3cUs3r3  
PASS=very_secret_password  
Since ftp servers usually work on clear-text protocol, the credentials are transmitted without encryption unless they use SSL/TLS(FTPS) or some other protocols to encrypt the data. 

<p align="center" width="100%">
    <img src="https://github.com/JothishKamal/task-7-cybersec/blob/main/images/GreenBlock.png?raw=true">
</p>

In packet 24, the user is uploading a JPEG file(flag.jpg) through the HTTP protocol. From the packets 25 to 29, we can see that packets of data are being transmitted and are finally reassembled in packet 30. Since, again, the data is transmitted without encryption we are able to get the flag.jpg by exporting the HTTP object.

<p align="center" width="100%">
    <img src="https://github.com/JothishKamal/task-7-cybersec/blob/main/images/FlagExport.png?raw=true">
</p>

Contents of flag.jpg:                                                                                                                               <p align="center" width="100%">
    <img src="https://github.com/JothishKamal/task-7-cybersec/blob/main/images/flag.jpg?raw=true">
</p>  
  
  
## Steps Taken:

1. Downloading and installing Wireshark.
2. Understanding the colors of each packet in Wireshark.
3. Looking for hidden data in the .pcap file.
4. Finding flag.jpg and exporting it as HTTP object (File -> Export Objects -> HTTP...).
# Problem 2
## Introduction:
Given is a .wav file that doesn't contain only sound.
## Tools used:
Spectrum Analyzer: https://academo.org/demos/spectrum-analyzer/
## Analysis:
Upon uploading the sound.wav file, we can see its spectrum containing the flag on the website.
<p align="center" width="100%">
    <img src="https://github.com/JothishKamal/task-7-cybersec/blob/main/images/WavFlag.png?raw=true">
</p>
By playing the audio completely, we can get the contents of flag.  

flag: e5353bb7b57578bd4da1c898a8e2d767  

The flag looks like a MD5 Hash.  

## Steps Taken:
1. Opening the sound.wav on Spectrum Analyzer.
2. Noting down the flag.
# Problem 3
## Introduction:
Given is an encrypted text file which contains whitespace characters.
## Tools Used: 
Microsoft VS Code (visualization of tabs and spaces), Binary Text to ASCII (https://www.rapidtables.com/convert/number/binary-to-ascii.html)
## Analysis:
Viewing the file in VS Code, we can see that there are **two** characters - tab and space.
<p align="center" width="100%">
    <img src="https://github.com/JothishKamal/task-7-cybersec/blob/main/images/EncryptedText.png?raw=true">
</p>

Replacing spaces with 0 and tabs with 1 and grouping 8 bits of Binary, we get something that looks like this:
<p align="center" width="100%">
    <img src="https://github.com/JothishKamal/task-7-cybersec/blob/main/images/DecryptedText.png?raw=true">
</p>

Running this through a Binary to Text Translator, we capture the flag:
<p align="center" width="100%">
    <img src="https://github.com/JothishKamal/task-7-cybersec/blob/main/images/DecryptedTextASCII.png?raw=true">
</p>    
flag: csi{not_all_spaces_are_born_the_same}

## Steps Taken:
1. Replacing space with 0 and tabs with 1.
2. Grouping 8 bits of Binary and delimiting them with spaces.
3. Running them through a Binary to Text Translator and capturing the flag.