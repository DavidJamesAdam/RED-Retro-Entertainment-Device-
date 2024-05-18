Here are various, quick and dirty walkthroughs of various things I used to work on RED, with various links associated with each topic. 
If you come across issues, please google it, there is a very strong likelyhood that others have come across the same problem. If you've done enough googling around, I'd be more than happy to help to the best of my ability. These steps are very specific to my computer and on Windows, so there's a chance you might need to approach certain steps a bit differently based on your OS and local machine.

Connecting to Raspberry Pi remotely. (Windows)
1. Make sure RaspberryPi is on
2. Open terminal
3. Type ssh "username"@"ipaddress"
4. Username is probably pi
  - Ip address can be found in RetroPi under Settings > Show ip
  - If it’s your first time connecting, you’ll have a prompt asking “are you sure you want to continue connecting?”
  - Type yes
5. Type in the password
  - Unless you’ve changed it, default password should be raspberry
- Connecting should be established and now you have remote access to RetroPi’s terminal where you can navigate file directories, download files, run scripts, etc.
- Good resource: https://www.makeuseof.com/how-to-ssh-into-raspberry-pi-remote/

Connecting to Raspberry Pi remotely from VS Code
1. Download the “remote-SSH” extension from the Extension tab in VS Code
2. Hover over the “SSH” and click the “+” button to the right to add the ip address to the list
3. Follow the prompts given by VS Code
- All the information you used to connect via terminal will be the same
- Now you can review/edit code without the hassle of using the terminal
- More in depth resource: https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh
https://code.visualstudio.com/docs/remote/ssh

Connecting to local server to check PiSugar battery
- "After finished, you can manage the battery by visiting http://<your raspberry ip>:8421 in your browser."
https://github.com/PiSugar/PiSugar/wiki/PiSugar2

How to backup a Raspberry Pi IMG
- This is a really good tutorial
  - Note: I could not find a version of Belena Etcher that had the “Clone Drive” option, so I used the Win32DiskImager
- https://www.makeuseof.com/how-to-back-up-your-raspberry-pi-sd-card-on-windows/
- Also a really important StackOverflow article if Win32DiskImager isn’t opening
https://stackoverflow.com/questions/63928864/win32diskimager-fails-to-launch

Getting script (controls.py) file onto the Raspberry Pi
- I like using Samba as all transfers happen in the file browswer, but there are other methods to transfer files from PC to the Pi
- https://www.dexterindustries.com/howto/how-to-transfer-files-to-your-raspberry-pi-from-a-pc-computer/

Running script on bootup
- You need to run the script when the Raspberry Pi first boots up as the script doesn't run automatically otherwise (and you need it to run to use the controls). I'm almost certain I used Crontab (although other methods exist) when I was finished with my script and didn't want to have to manual run it everytime I booted up the Pi.
- https://www.dexterindustries.com/howto/auto-run-python-programs-on-the-raspberry-pi/

# Getting the analog joystick to work
This was maybe one of 2 biggest challenges when making RED (the other challenge was teaching myself Fusion 360 to design the case).  
Almost every forum post/reddit post/resource I came across either was a complete dead end or had incomplete/unreadable/outdated resources. I hope to make this section as comprehensive as I can as this is the one thing I'm getting the most questions about.  
There are a number of things to consider about the joystick:
- It's an **analog** joystick and the Pi **only** accepts digital input, meaning you need to get an Analog to Digital Converter (ADC for short). The X/Y values will go into the input pins of the ADC, with the output pins going to the Raspbery Pi GPIO pins.
- Here's a picture I drew to help me remember what pins go to what GPIO pins
  - Please note: the GPIO pins refer to just that, the GPIO pins, not the **actual physical pins** on the Raspberry Pi. Refer to a pin diagram of the Raspberry Pi 4b to know where the pins are located.
![IMG_0259](https://github.com/DavidJamesAdam/RED-Retro-Entertainment-Device-/assets/51091241/bed422f1-5937-4172-a26c-7c0181f40f61)
- Really, the directional values can go into any channel on the input side, but it's easiest to put the x values (left/right) in channel 0 and y values (up/down), into channel 1, but where you ultimately put those values it up to you.
- The GND on the joystick will go to GND
- 3.3V power should go to which ever pins power the joystick on the joystick itself (on the Parallax joystick I'm using, it's the L/R+ and U/D+ pins, the labeling on your joystick might be different).

At this point, if you have everything wired up correctly and you have the script running, the joystick *should* work (along with other buttons you have plugged into the GPIO pins (A, B, X, Y, D-pad, etc)). I say should because there are a lot of factors in play to get the joystick to function properly. As of writing this current update (May 18th, 2024), this is more or less the only way I have found out how to get an analog joystick to work with the Raspberry Pi using Python. I will be updating this how-to over the next few weeks with more pictures and precise information as I think of things and dismantle the current version of RED to redesign and build version 2.  
  
At the very least, I hope this gets you started. And please remember, if you come across an issue **please google it first**. If you've done all you can and still can't figure out an issue, I would be more than willing to help to the best of my ability.  

Once I dismantle RED MKI, I will be implementing and testing a second joystick, but that's not for quite some time.

