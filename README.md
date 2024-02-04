# libcamera-in-container
Demonstration on how to get `libcamera` working in a container

## run demo
```
docker-compose up
```

> ![IMPORTANT]
> You may have to run the demo as root (or set up permissions),
> lest `cam` (in the container) won't have read access to the cameras!

## clean up demo
```
docker-compose down
```


# What's going on?
The build compiles libcamera [by the books](https://libcamera.org/getting-started.html) and installs dbus.
This gives us the `cam` application, which can enumerate libcamera devices `cam -l`

Getting libcamera working in containers is just a matter of dabbling with dbus.
To do this I gave the container full access to `/run/udev`.
And voilà, libcamera works :)

Do note that you may have to set up permissions for your container (cam will say it has no r/w permission).
*Or* you can just run the container as root.
