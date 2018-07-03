dummy-boshrelease
=================

A very simple [BOSH](https://github.com/cloudfoundry/bosh) release.

### 0. Usage

* Upload the Dummy BOSH release to the BOSH director using BOSH cli v2 and a configured [enviroment](https://bosh.io/docs/cli-envs.html):
```
bosh upload-release https://github.com/pivotal-cf-experimental/dummy-boshrelease/releases/download/v2/dummy-2.tgz
```
* Update the BOSH director's [cloud-config](http://bosh.io/docs/cloud-config.html)
  * create a *network* named *manual*
  * create a *vm_types* named *tiny*
  ```
  vim cloud-config.yml # add 'manual' network and 'tiny' vm_type
  bosh update-cloud-config cloud-config.yml
  ```
* Copy the
  [sample manifest](https://raw.githubusercontent.com/pivotal-cf-experimental/dummy-boshrelease/master/templates/dummy.yml):
```
curl -OL https://raw.githubusercontent.com/pivotal-cf-experimental/dummy-boshrelease/master/templates/dummy.yml
bosh deploy -d dummy dummy.yml
```

### 1. BOSH Jobs

Dummy BOSH release has the following jobs:

1. `dummy` has no packages and only 1 job that monitors pid 1.

1. `dummy_with_package` also has 1 job but depends on 1 package.

1. `dummy_with_properties` has no packages and only 1 job that
   monitors 1 pid, however it has a property that can be altered
   to allow you to iterate rapidly on bosh deploys.

1. `dummy_fail_eventually` has no packages and only 1 job that
   monitors a process that exits after 5 seconds.

1. `dummy_fail_immediate` has no packages and only 1 job that
   does not record a PID and exits immediately.

1. `dummy_errand` has no packages and echo to stdout

1. `dummy_with_link` provides a link named `link_from_dummy`

Use `dummy-boshrelease` to create a deployment manifest more easily, especially handy if it's your first time
creating a deployment manifest.

Its simplicity also makes it a good way to learn the shape of a BOSH release.

TIP: Use it with [bosh-lite](https://github.com/cloudfoundry/bosh-lite) to make setting up your first BOSH deployment even easier!
