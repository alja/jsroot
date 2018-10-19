
# Web-EVE User guide

This document is a brief description of web-based event display framework Web-EVE. It presumes user is familiar with originating X11 implementation of event visualization envenironment [EVE](https://root.cern.ch/doc/v614/group__TEve.html).

This code is at the experimental stage. 

#### Eve Elements
In this release we support the following Eve elemets:
  * REveTrack
  * REveLines
  * REvePointsSet
  * REveCoimpund
  * REveJetCone
  * REveGeoShape
  
#### Projections
 Projections have been imported from original implementation restoring complete functionality:
   * propagating changes from projectable to projected elements
   * nonlinear scaling 
  
#### Viewers  
 Scenes and Viewers are created on the server the same way as in X11 implementation of EVE. Please see eamples in eve7 tutorials.
 So far window management is not completed. All viewers (GL or Table) are automatically streamed and displayed on the client side. The first created view takes the main slot, all other views are stacked in the vertical side slot.
 <br/>
 


 | [![EventDemo](https://genki.physics.ucsd.edu/alja/eventdemo-scaled.png)](event-demo.png) | 
|:---:|
| Screenshot of web event display in chrome browser| 
 
#### Physics collections
The original EVE package has no support for management and display of
experiment-specific physics collections. EVE objects were always just
a visual representation of physics objects. Now that physics collections are avilable in ROOT, one can
 *  Provide filtering of physics objects on the level of physics collection.
 * Support Table views with arbitrary expressions for each column.

<a href="url"><img src="https://genki.physics.ucsd.edu/alja/collection.png"  width="550" ></a>

#### Dynamic Tables

In the server-client model, it is possible to edit tables in the
runtime. A user can change physics collections. The columns can be
modified as well. On can edit existing column expression or add a new
column with any valid expression.
<br/>
<!--a href="url"><img src="https://genki.physics.ucsd.edu/alja/table.png"  width="550" ></a-->
| [![EventDemo](https://genki.physics.ucsd.edu/alja/table-scaled.png)](table-large.png) | 
|:---:|
| Adding new column in table. Use i. to access element fimction | 

## Server configuration
### Window mapping
Browser windows are mapped by the default. One can disable the behaviour by adding the following line in .rootrc file:
> WebEve.DisableShow: 1

### Port number
The port is picked randomly in the range in the default port range (8800 - 9800). One can fixed it in .rootrc file 
> WebGui.HttpPort:            8800

### Running remotely
When user runs web event dispaly remotely it has to disable mapping of window with Eve7.DisableShow. It is also recommended to use fixed port. Below is a content of a typical .rootrc:
> WebEve.DisableShow: 1
> WebGui.HttpPort:            9090

### Browser cache
Browsers cache content with pages with same URL. There are two ways to empty cache:

#### Manually with browser plugins:

  Chrome plugin Clear Cache:
  ![alt text](https://genki.physics.ucsd.edu/alja/clearcache-icon3.png "Chrome clear cache plugin")
  
  Firefox plugin Empty Cache:
  ![alt text](https://genki.physics.ucsd.edu/alja/emptycache-icon2.png "Firefox clear cache plugin")
  
#### Automtically 
 One can disable browser cache in .rootrc
  > WebGui.HttpMaxAge: 0

### Secure protocol
Some of the browser allow only https protocol. In this case certificate has to be specified 
> WebGui.ServerCert:          /path/to/server.pem


### Closed Firewall
In some cases like lxplus or lpcnodes do not allow open ports. In this case user has to create a ssh tunnel. Below is an example how to create a tunnel from lxpls067.cern.ch to localhost on port 1234.


> ssh -nNT -L 1234:localhost:8800 lxplus067.cern.ch 

The url used on your local desktop will therefore be:

> http://localhost:1234/web7gui/win1/

