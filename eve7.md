## Web based event visalization environment EVE-7
This document is a bried description of web based event display framework. IT helps user to set default behaviour and
new features that were not included in X11 version.

This code is still in experimental stage.

## Default behaviour
### Window mapping
Browser windows are mapped by the default. One can disable the behaviour by adding the following line in .rootrc file:
> Eve7.DisableShow: 1


### Http server port
The port is picked randomly in the range in the default port range (8800 - 9800). One can fixed it in .rootrc file 
> WebGui.HttpPort:            8800

### Running remotely
When user runs web event dispaly remotely it has to disable mapping of window with Eve7.DisableShow and set fixed port. In some cases like lxplus or lpcnodes firewall closes the ports. In this case user have to create a ssh tunnel. For example this 
creates a tunnel from lxpls067.cern.ch to localhost on port 1234:

> ssh -f -L 1234:localhost:8800 lxplus067.cern.ch sleep 10000
The url used on your local desktop will therefore be:
> http://localhost:1234/web7gui/win1/


