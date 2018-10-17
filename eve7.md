
# User guide

This document is a bried description of web based event display framework EVE-7. It presumes user is familiar with originating X11 implemetation of event visaulization evenironment [EVE](https://root.cern.ch/doc/v614/group__TEve.html).

This code is at experimental stage. 

#### Eve Elements
In this release we support the following Eve elemets:
  * REveTrack
  * REveLines
  * REvePointsSet
  * REveCoimpund
  * REveJetCone
  * REveGeoShape
#### Projections
  
#### Viewers  
 Scenes and Viewers are created the same as in X11 implemtatopn of EVE. PLase see eamples in eve7/tutorials.
 So far window management is not complited. All viewers (GL or Table) are automatically streamed and disaply on the client side.The first created view takes the main slot, all other views are stacked in the vertical side slot.
 
  <a href="url"><img src="https://genki.physics.ucsd.edu/alja/event-demo.png"  width="550" ></a>

#### Physics collections
Original EVE package has no support for management and display of
experiment-specific physics collections. EVE objects were always just
a visual representation of physics objects.
From experiance with otherevent displays we saw Physics Collections and Event
Items are essential to Fireworks data management and display. This is
the reason we have implemented that in EVE-7 from the early
start. 

<a href="url"><img src="https://genki.physics.ucsd.edu/alja/collection.png"  width="550" ></a>

#### Dynamic Tables

In the server-client model it is possible to edit tables in the
runtime. A user can change physics collections. The columns can be
modified as well. On can edit existing column expression or add a new
column with any valid expression.
<br/>
<a href="url"><img src="https://genki.physics.ucsd.edu/alja/table.png"  width="550" ></a>

## Default behaviour
### Window mapping
Browser windows are mapped by the default. One can disable the behaviour by adding the following line in .rootrc file:
> Eve7.DisableShow: 1


### Port number
The port is picked randomly in the range in the default port range (8800 - 9800). One can fixed it in .rootrc file 
> WebGui.HttpPort:            8800

### Running remotely
When user runs web event dispaly remotely it has to disable mapping of window with Eve7.DisableShow. The URL is pasted to the local browser to display content.

##### Secure protocol
Some of the browser allow only https protocol. In this case certificate has to be specified 
> WebGui.ServerCert:          /home/xxx/server.pem


##### Closed Firewall
Wand set fixed port. In some cases like lxplus or lpcnodes firewall closes the ports. In this case user have to create a ssh tunnel. For example this 
creates a tunnel from lxpls067.cern.ch to localhost on port 1234:

> ssh -f -L 1234:localhost:8800 lxplus067.cern.ch sleep 10000

The url used on your local desktop will therefore be:

> http://localhost:1234/web7gui/win1/
