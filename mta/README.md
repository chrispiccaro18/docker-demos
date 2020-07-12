# MTA (Migrating Traditional Apps)

## Commands

### Bind Mount

To bind-mount (link directories in the host to the app):
When building: `-v <path-in-host>:<path/in/app>`

Example: the app expects in/ dir to be on same level but we want it to be in the host:
`docker run -v $(pwd)/in:/app/in <image-name>`

### Last Container Ran

`docker ps -l`

## Amazing Image Changer

 This command line app scans for images in ./in folder,
 and turns them into chalk-looking images in ./out folder,
 then exits.

 It logs to two files in ./logs using Winston module

 It requires node v8.x

 The server need to have GraphicsMagick installed, so
 you might need to do something like installing with apt:

 `apt-get install -y graphicsmagick`

 index.js is the main entrypoint
