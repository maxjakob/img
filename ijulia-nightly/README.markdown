# ijulia nightly

An ijulia installation. Get purzelrakete/img/bin/ijulia to start it.

## caveats

Currently not actually a nightly build. need to trigger builds:

    curl --data "build=true" -X POST \
      https://index.docker.io/u/purzelrakete/img/trigger/secret-uid

If your are using boot2docker on OSX, you may have to fiddle with forwarded
ports [0].

[0] - https://github.com/boot2docker/boot2docker/blob/master/doc/WORKAROUNDS.md
