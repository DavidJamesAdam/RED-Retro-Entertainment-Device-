Here are various, quick and dirty walkthroughs of various things I used to work on RED, with various links associated with each topic. 
If you come across issues, please google it. If you come across a problem, there is a very strong likelyhood that others have come across the same problem.

Connecting to Raspberry Pi remotely. (Windows)
1. Make sure RaspberryPi is on
2. Open terminal
3. Type ssh <username>@<ipaddress>
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
