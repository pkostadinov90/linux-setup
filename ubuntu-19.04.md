# Steps for Ubuntu

* ## Adding Bulgarian Typewriter

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
	* ### Resources
		* https://askubuntu.com/questions/510024/what-are-the-steps-needed-to-create-new-keyboard-layout-on-ubuntu
		* https://forums.linuxmint.com/viewtopic.php?t=228743
		* http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11

* ## Sublime
	All of my sublime setup is in https://github.com/pkostadinov90/sublime-text-3-sync
	
	Resources:
		* https://forum.sublimetext.com/t/what-s-the-best-way-to-backup-the-st3-configuration/25494

* ## Vagrant
	* ### Install Prerequierements
		```
		sudo apt-get install vagrant
		sudo apt-get install virtualbox
		sudo apt-get install virtualbox-guest-x11
		```
	
	* ### Common commands
		* `vagrant up` - start and compile
		* `vagrant halt` - shutdown
		* `vagrant ssh` - ssh to the virtual machine

