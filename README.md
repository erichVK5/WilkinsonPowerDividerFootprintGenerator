# WilkinsonPowerDividerFootprintGenerator
A Wilkinson Power Divider Footprint Generator for gEDA and Kicad.


Those wishing to use the utility will need to install the java compiler javac, and a compatible java virtual machine (JVM).

Having cloned the git repository to a local directory, i.e.

	git clone https://github.com/erichVK5/WilkinsonPowerDividerFootprintGenerator

	cd WilkinsonPowerDividerFootprintGenerator

You can then compile the java source code:

	javac WilkinsonPowerDividerFootprintGenerator.java

Tips:

The utility adds input and output pads in the final three lines of the footprint file. Users will need to specify their dimensions to achieve the required stripline impedance relative to the power divider arms.

Users may wish to experiment with segment lengths to achieve a suitably rounded contour, and dimensions should be verified before sending off designs for fabrication.

The velocity factor of the PCB material will affect the dimensions and electrical length of the divider arms.

Usage:

	java WilkinsonPowerDividerFootprintGenerator -option value

		-k			export a kicad module, default is geda .fp file

		-r long	 	length of resistor gap in microns

		-f double	frequency of operation in Megahertz

		-w long		track width in microns

		-t long         input/output(s) terminal length, in microns, default is zero length

		-p long		input/output port track width in microns
					default: port track width = track width

		-v double	velocity factor <= 1.0
					default: 1.0

		-l long		length of segment used to approximate circular arc in microns

		-h			prints this

Example usage:

	java WilkinsonPowerDividerFootprintGenerator -r 2000 -f 1800 -w 3000 -l 2000 -v 0.76 -p 4200 -k -t 1200

	generates a wilkinson power divider with two arms, each
	lambda/4 in length, assuming a substrate velocity factor
	of 0.76, separated by a "resistor gap" of 2000 microns,
	divider arm track width of 3000 microns, input and output
	track widths of 4200 microns and lengths 1200 microns, and
	using segment lengths of 2000 microns to create the arc
	segments in a kicad module.

