# RaspberryPi Scan Station

This implements a Raspberry Pi based scan station. The image is based on
[scanbd](https://sourceforge.net/projects/scanbd/) and
[sane](http://www.sane-project.org/). By default, the configuration arranges to
trigger the `action.script` in the directory `/usr/share/scanbd/scripts` of the
image.

To be able to scan, you should give the container [access][1] to the USB
subsystem, using a command similar to the following:

    docker run -it --rm --device /dev/bus/usb efrecon/armv7hf-scan

The container exposes two volumes that you might want to mount somewhere else in
order to either collect the scans or to perform more complex operations:

- `/var/spool/scan` is the default location where the script that is triggered
  on button presses will be storing the scanning results.

- `/usr/share/scanbd/scripts` is the directory location of the `action.script`
  that is triggered for all button presses. You could place your own script if
  you wanted to implement more complex operations. The container already
  contains an installation of [ImageMagick][2] and [Tcl][3] to help in ironing
  out more complex tasks.
  
  
[1]: https://docs.docker.com/engine/reference/run/#/runtime-privilege-and-linux-capabilities
[2]: http://www.imagemagick.org/
[3]: http://www.tcl-lang.org/