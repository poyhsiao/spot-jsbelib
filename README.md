spot-jsbelib
============

The purpose of the javascript library is providing the event driven beacon framework, trigged by beacons and thier distance around user's device.

www.spot.ms


Installation
------------

This library only depends on jQurey library. Developers would include the jQuery library and spot-jsbelib.js in the HTML header, like this:

	<script	type="text/javascript" src="jquery.min.js"></script>	
	<script type="text/javascript" src="spot_jsbelib.js"></script>

Usage
-----

Create the instance.

	var beaconManager=new spotJsBEL();

Set the evnet handler.

	var beaconHandler = function(beaconArray) {
		// Do-Something with beaocn array
	};
	beaconManager.onBeaconChanged(beaconHandler);


Initialize the instance after dom ready.

	$(window).ready(function() {
		beaconManager.init();
	};

Beacon Array
------------

When beaconChanged event callback function is called, it passed a beacon array as parameter.

beacon array contains json objects to preset the detected beacon data:
{id:<String>, name: <String>, px: <Number> }
* id and name: using by Spot cloud service, or your own definition.
* px: based on Apple's iBeacon specification, proximity values indicate:
	* 0 : Unknown (> 30 m )
    * 1 : Immediate (< 50 cm)
    * 2 : Near (< 2 m)
    * 3 : Far (< 30 m)

Notice: You may not get the px value 0, when beacon is far away and then no more exist in the array list.


Testing your Code
-----------------

You can use the function updateBeaconData in the browser's console to update the beacon array manually, if you don't have beacon hardware.
An [example code on jsfiddle](http://jsfiddle.net/kklabs/J6B2Z/), input the following javascript in browser's console (target to jsfiddle's iframe)

	beaconManager.updateBeaconData('{"b":[{"id":"1-1-1", "name":"test", "px":2}],"d":true,"o":true}');



