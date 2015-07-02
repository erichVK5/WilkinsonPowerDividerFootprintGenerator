# WilkinsonPowerDividerFootprintGenerator
A Wilkinson Power Divider Footprint Generator for gEDA and Kicad.


Those wishing to use the utility will need to install the java compiler javac, and a compatible java virtual machine (JVM).

Having cloned the git repository to a local directory, i.e.

	git clone https://github.com/erichVK5/WilkinsonPowerDividerFootprintGenerator

	cd WilkinsonPowerDividerFootprintGenerator

You can then compile the java source code:

	javac WilkinsonPowerDividerFootprintGenerator.java

Tips:

The utility adds input and ouput pads in the final three lines of the footprint file. Users will need to modify these to achieve the required impedance relative to the power divider arms. Users may wish to experiment with segment lengths to achieve a suitably rounded contour, and dimensions should be verified before sending of designs for fabrication.


Usage:

	java WilkinsonPowerDividerFootprintGenerator -option value

		-k	export a kicad module, default is geda .fp file

		-r long	 length of resistor gap in microns

		-f long	 frequency of operation in Megahertz

		-w long	 track width in microns

		-l long	 length of segment used to approximate circular arc in microns

		-h	 prints this

Example usage:

	java WilkinsonPowerDividerFootprintGenerator -r 2000 -f 1800 -w 3000 -l 2000 -k

	generates a wilkinson power divider with two arms, each
	lambda/4 in length, separated by a "resistor gap" of
	2000 microns, track width of 3000 microns, and using
	segment lengths of 2000 microns to create the arc
	segments in a kicad module.

