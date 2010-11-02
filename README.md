Installation :
--------------
- copy the script into your minecraft server folder.
- allow the script to be executed ( chmod +x minecraft.sh )
- check the rights of the script user. Every folder specified in the configuration phase has to be available to him.
- edit the script to configure it (see the configuration section)

(optional)
- I strongly recommend using crontab to automate some of the process. I prefer to perform logs + cartography + server restart at 4AM 
every day. The 'logs' command should always be used BEFORE a restart, as the restart wipes the previous logs. I'm running hey0's servermod, which 
allows to have a log history, but thats not the case for everyone.
- I also recommend setting an Internet public folder, for the maps images to be displayed. People on my server love this feature, as they 
know a new map is generated every day, and they can see the evolution of our world.
- I made an alias to be able to use 'minecraft command' instead of './mincraft.sh command'. It also enables the automatic completion, if you type 'mine' then press tab. Much quicker =) You can do this by 
editing /home/USER/.bashrc, and adding the line --> alias 
minecraft="/home/minecraft/minecraft.sh" <-- (of course, change the path if needed)


Configuration :
---------------

      There are several variables to set before you can run the script 
for the first time.
      Open minecraft.sh with a text editor, and edit the following 
lines, at the beginning of the file :

          o MC_PATH=/home/minecraft
            This is the path to your minecraft folder
          o SERVERMOD=0
            If you are running hey0's servermod, this needs to be set to 
1 (better logging and automatic updating of the mod)
          o RUNECRAFT=0
            If you want your script to update runecraft automatically 
too, set this to 1
          o WORLD_NAME="world"
            This is the path to the world folder
          o SCREEN_NAME="minecraft"
            This is the name of the screen the server will be run
          o MEMALOC=1024
            This is the size of RAM you want to allocate to the server
          o DISPLAY_ON_LAUNCH=1
            Do you want the screen to be displayed each time the server 
starts ? 1 if yes, 0 if no.
          o BKUP_PATH=$MC_PATH/backup
            This is the path to the backup folder. Map backups and old 
log entries will go there.
          o BKUP_DAYS=3
            How long will the map backups be kept ? (Only used with the 
'./minecraft.sh backup clean' command)
          o CARTO_PATH=$MC_PATH/carto
            This is the path to c10t's cartography script
          o MAPS_PATH=/var/www/minecraftMaps
            This is the path to the world maps folder
          o LOG_TDIR=/var/www/minecraftLogs
            This is the path to the logs folder
          o LOGS_DAYS=7
            How long will the logs be kept ? (Only used with the 
'./minecraft.sh logs clean' command)


    * Detailed Usage :

o ./minecraft.sh
            Without arguments, the script will resume the server screen. 
(If you want to close the screen without shutting down the server, use 
CTRL+A then press D to detatch the screen)
o ./minecraft.sh status
            Tells you if the servers seems to be running, or not.
o ./minecraft.sh start [force]
            Starts the server. If you know your server is not running, 
but the script believe it is, use the force option.
o ./minecraft.sh stop [force]
            Self explainatory
o ./minecraft.sh restart [warn]
            If the warn option is specified, it will display a warnning 
30s & 10s before the restart happens.
o ./minecraft.sh logs [clean]
            Parses logs into several files, grouped into a folder named 
with the date of the logging.
            If the clean option is specified, it will move the older 
folders into the backup folder.
            Again, this command should be issues before a server 
restart.
o ./minecraft.sh backup [clean]
            Displays a message to the players if the server is online, 
stops the writing of chunks, create a dated archive and backs up the 
world folder.
            If the clean option is specified, it will delete the older 
archives.
o ./minecraft.sh cartography
            Displays a message to the players if the server is online, 
stops the writing of chunks, initiates c10t's cartography script.
            I strongly recommend the MAPS_PATH to be a internet public 
folder.
o ./minecraft.sh update
            Stops the server if it is online, backs up the old 
binairies, downloads the last binaries from mincraft.net and restarts 
the server.


    * Future updates :
      Bugfixes ?
      Better log parsing, this one is realy primitive
      Anything you could think of.


Any advice on how to upgrade this script is very welcome.
