dummy-boshrelease
=================

A very simple [BOSH](https://github.com/cloudfoundry/bosh) release.

It has only 2 job templates:

1. `dummy` has no packages and only 1 job that monitors pid 1.
2. `dummy_with_package` also has 1 job but depends on 1 package.

Use `dummy-boshrelease` to create a deployment manifest more easily, especially handy if it's your first time
creating a deployment manifest.

Its simplicity also makes it a good way to learn the shape of a BOSH release.

TIP: Use it with [bosh-lite](https://github.com/cloudfoundry/bosh-lite) to make setting up your first BOSH deployment even easier!
