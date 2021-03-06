QGIS epanet plugin
==================

Extends processing framework to models the hydraulic and water quality behavior of water distribution piping systems

This plugin lets you model hydraulic network for water and run simulations to get water pressure informations and more.

See a demo screencast here :

https://vimeo.com/87754967

Requirements
============

You need :
* A working version of Epanet (english version mandatory)
* QGIS > 2.0
* The QGIS Processing framework
* Python module matplotlib

Installation
============

You need to have epanet as a command line tool for the plugin to work.

Install Epanet for Windows
--------------------------

Download and run https://www.epa.gov/sites/production/files/2014-06/en2setup_0.exe


Compile Epanet for linux
------------------------

Download Epanet sources from http://www2.epa.gov/sites/production/files/2014-06/en2source.zip

For linux:

    mkdir epanet
    cd epanet
    wget http://www2.epa.gov/sites/production/files/2014-06/en2source.zip
    unzip en2source.zip
    unzip -n epanet2.zip 
    unzip -n makefiles.ZIP
    unzip -n GNU_EXE.ZIP

Open the file epanet.c, comment out the line

    #define DLL

and uncomment the line

    #define CLE

The file should look afterwards like:

    #define CLE     /* Compile as a command line executable */
    //#define SOL     /* Compile as a shared object library */
    //#define DLL       /* Compile as a Windows DLL */

Open the file Makefile and replace the line

    cc -o epanet2 -lm $(objs)

by

    cc -o epanet2 $(objs) -lm 

Then run: 
 
    make

Install the plugin
------------------
 
Simply put this directory in the plugin directory. On linux:

    cd ~/.qgis2/python/plugins
    git clone https://github.com/Oslandia/qgis-epanet.git

You then need to run QGIS, install the processing plugin and configure the path to the epanet executable in QGIS menu Processsing->Options and configuration.

Note:
    On Windows, choose epanet2d.exe.

Testing
=======

The file simple_network.zip contains an example of a tank emptying on a pipe. Unzip the directory en follow intructions in  simple_network/README.md

Notes
=====

This plugin has been tested on real data on a real use case. This use case cannot be made publicly available.

We are currently looking for a use case with data that can be published alongside the code.

Credits
=======

This plugin has been developed by Oslandia ( http://www.oslandia.com ).

Oslandia provides support and assistance for QGIS and associated tools, including this plugin.

This work has been funded by European funds.
Thanks to the GIS Office of Apavil, Valcea County (Romania)

License
=======

This work is free software and licenced under the GNU GPL version 2 or any later version.
See LICENSE file.

