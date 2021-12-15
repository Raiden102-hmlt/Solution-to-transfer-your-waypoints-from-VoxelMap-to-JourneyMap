# Solution-to-transfer-your-waypoints-from-VoxelMap-to-JourneyMap
Easy solution to transfer your waypoints from VoxelMap to JourneyMap, like easy easy

INTRODUCTION (you can skip it):

  Firstly, you don't need to know any python to use it or do anything complicated, a 5yo could do it.
So i wanted to migrate from VoxelMap to JourneyMap, but since the waypoints format is different, it's a fastidious work to do it by hand.

  Because it's boring and it might help some people as well, I wrote a Python script that will take your single VoxelMap waypoints file : world.points (in C:\Users\[your name]\AppData\Roaming\.minecraft\voxelmap), and create all the waypoints files needed in the directory needed (which will be C:\Users\[your name]\AppData\Roaming\.minecraft\journeymap\data\sp\[your world]\waypoints).

You can access these easily with Win+R and search %appdata%

========================================================================================================================================================================

SOLUTION :

 You will need to have Python installed (not an online version), no need to install any library, and just do these simple steps :

1 : Open your world.points file (VoxelMap) with a text editor such as notepad

2 : Copy it all and paste it at the beginning of the python code : chain = '''[your waypoints]'''

3 : Find the folder name where your JourneyMap waypoints are saved (C:\Users\[your name]\AppData\Roaming\.minecraft\journeymap\data\sp\[your world]\waypoints)

4 : Copy/paste that directory at the beginning : directory = [your directory]

5 : Press F5 to launch the program, you should have them all in the desired folder and your can now enjoy your world with the waypoints !

========================================================================================================================================================================

VERY IMPORTANT NOTES !!! (READ THEM IF YOU WANT IT TO WORK, LIKE REALLY)

1 : Change the \ in your directory address to / or else it will not work !!! Example : C:\Users\ will become C:/Users/

2 : If your waypoint has a ?, a @ or some weird characters, remove them beforehand, the code will tell you which name isn't working at the end

3 : The VoxelMap waypoints file format was such as this => name:House,x:80,z:224,y:128,enabled:false,red:0.0,green:0.9137255,blue:0.078431375,suffix:key,world:,dimensions:the_nether# Remove all text that isn't that format (subworlds:, oldNorthWorlds:, seeds:)
Hopefully you have the same, else DM me so I can help you with it, and the JourneyMap format was : (see photo attachment)

4 : I posted this on StackOverflow as well, check the times of publication (identical) before accusing me of stealing my own work :)

5 : It will fail if you have your waypoints_text as: waypoints_text = '''[your waypoints] ''' and not as : waypoints_text = '''[your waypoints]'''

(Edit : i did more coding so now it will also factor in the world in which your waypoints were and if they were enabled or not, was kinda long but worth it i guess)

========================================================================================================================================================================

CODE : (NB n°1 : not optimized at all because I did it on the go so don't mind it // NB n°2 : copy everything below until the end)
Copy the code here since Reddit does weird stuff with Entry and Tab...
