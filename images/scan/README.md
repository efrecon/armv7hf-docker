# RaspberryPi Scan Station

This implements a Raspberry Pi based scan station. The image is based on
`scanbd` and `sane`. The configuration arranges to trigger the `action.script`
in the directory `/usr/share/scanbd/scripts` of the image. Change this to
implement your own actions.  To start this you should:

    docker run -it --rm --privileged -v /dev/bus/usb:/dev/bus/usb efrecon/armv7hf-scan

This is a work-in-progress and might not work for the time being and until
documentation has been finalised.