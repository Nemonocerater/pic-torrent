
#Implementation

###Server

/getImage/<originalURL>
* This returns the image as a normal download and adds the requester to the torrent pool
* If #nodesInPool > threshold send back torrent message and peers to download from.

Need to find a way to scale the server, so that a single server doesn't get overloaded with requests.

###Client

Send the client the original URL to the image.  Instead of requesting the image from the server like normal, you ping the server with the original URL.  It will download the image and then send it back to you.  It will also add you as a client to the pool.  If there were enough other clients serving that image up, then it would ask you to download it from them.

Need to make sure that the images that are most likely to be seen are the ones getting priority to be downloaded. `getImage('...url...', priority)`

###Testing

####My Testing

I need to have a way to spin up a lot of fake [android](http://stackoverflow.com/questions/1761246/possible-to-safely-run-multiple-android-emulators-on-the-same-machine-and-commun) and ios devices.

Maybe I could launch a super simple stupid app that shows images to people using this system to display the images.

####Their Testing

Load splash screen, logo, etc.  Some image that shows up a lot (if it's loaded from the server).  The key is finding a single image they can load that they can test in a patch update, so as to not break their whole app.

Do Google-esque stuff and make a 'special' logo for one patch that is built into the code, but override it with the normal image when it loads.  Or just ping graphite to say that you have received the image.

