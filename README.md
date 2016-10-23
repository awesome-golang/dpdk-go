# Go bindings for DPDK

[![Build Status](https://travis-ci.org/feiskyer/dpdk-go.svg?branch=master)](https://travis-ci.org/feiskyer/dpdk-go) [![Go Report Card](https://goreportcard.com/badge/github.com/feiskyer/dpdk-go)](https://goreportcard.com/report/github.com/feiskyer/dpdk-go)

## Install dpdk and dpdk-go

Setup `RTE_TARGET`, `RTE_SDK` and `DPDK_VERSION` in `hack/dpdk.rc`, then run

```sh
hack/dpdk-install.sh
source hack/dpdk-util.sh
init-dpdk`
go get -u github.com/feiskyer/dpdk-go
```

Notes: If dpdk is installed inside a virtual machine, (e.g. VMWARE), then patch `hack/vmware.diff` must be applied before compling the dpdk source.

## Install dpdk-ovs

Install dpdk first, then run

```sh
hack/ovs-install.sh
source hack/dpdk-util.sh
init-dpdk
start-ovs
```

## DPDK samples

### [Helloworld](http://dpdk.org/doc/guides/sample_app_ug/hello_world.html)

```sh
go get -u github.com/feiskyer/dpdk-go/samples/helloworld
helloworld -c3 -n1
```

### [skeleton](http://dpdk.org/doc/guides/sample_app_ug/skeleton.html)

A simple skeleton example of a forwarding application.

```sh
go get -u github.com/feiskyer/dpdk-go/samples/skeleton
skeleton -c3 -n1
```

### [Exception Path](http://dpdk.org/doc/guides/sample_app_ug/exception_path.html)

Reads packets from `dpdk port 0`, and then write the data to `tap_dpdk_00`:

```sh
go get -u github.com/feiskyer/dpdk-go/samples/exception-path
exception-path

# in another terminal
tcpdump -nn -i tap_dpdk_00
```

## Acknowledgement

Performance is not guaranteed because of less tests.
