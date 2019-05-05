# Steps for Ubuntu

## Adding Bulgarian Typewriter

* ### file `/usr/share/X11/xkb/symbols/bg`

	You need to clone the block:

	```
	default  partial alphanumeric_keys
	xkb_symbols "bds" {
	```

	And change:

	* Remove the `default` key word
	* Rename `bds` to `bdstw`
	* Update the following key bindings:

		```
		key <TLDE> {[ grave,             asciitilde,        bracketleft,       bracketright        ]};
		key <AE11> {[ minus,             I,                 U2011,             EuroSign            ]};
		key <AE12> {[ period,            V                                                         ]};
		key <AC01> {[ Cyrillic_softsign, U042C,             Cyrillic_yeru,     Cyrillic_YERU       ]};
		key <BKSL> {[ parenleft,         parenright,        guillemotleft,     guillemotright      ]};
		```

	* Run `sudo dpkg-reconfigure xkb-data` to reload the layout. A restart would be required, however do this at the end of all steps.

* ### file `/usr/share/X11/xkb/rules/evdev.xml`

	You need to find the block containing `<name>bg</name>`. You need to add to it the Bulgarian Typewrites under the `variantList`:
	
	```
	<variant>
	  <configItem>
		<name>bdstw</name>
		<description>Bulgarian Typewriter</description>
	  </configItem>
	</variant>
	```

* ### file `/usr/share/X11/xkb/rules/xorg.lst`

	You need to add the new layout aroung the other `bg:` rows:
	
	```
	bdstw           bg: Bulgarian Typewriter
	```

* ### Reboot
