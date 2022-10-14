# Aurae

Aurae is a free and open source Rust project that houses a generic systems runtime daemon built specifically for enterprise distributed systems such as Kubernetes, and microVM hypervisor deployments.

Think of [auraed](https://github.com/aurae-runtime/auraed) as a pid 1 init machine daemon with a scope similar to [systemd](https://www.freedesktop.org/wiki/Software/systemd/) and functionality similar to [containerd](https://github.com/containerd/containerd) and [firecracker](https://github.com/firecracker-microvm/firecracker).

Aurae brings [SPIFFE](https://github.com/spiffe)/[SPIRE](https://github.com/spiffe/spire) (x509 mTLS) backed identity, authentication (authn) and authorization (authz) as low as the Unix domain socket layer in a distributed system.

Aurae exposes its functionality over a gRPC API which is referred to as the [Aurae Standard Library](https://github.com/aurae-runtime/auraed/tree/main/stdlib#the-aurae-standard-library).

A single Aurae instance has no awareness of higher order scheduling mechanisms such as the Kubernetes control plane, or other scheduling and scaling mechanisms. Aurae is designed to take ownership of a single machine, and expose the standard library a generic and meaningful way for higher order consumers.


### Motivation 

Read [Why fix Kubernetes and Systemd](https://medium.com/@kris-nova/why-fix-kubernetes-and-systemd-782840e50104) by [Kris Nóva](https://github.com/krisnova). 

Aurae attempts to simplify and improve the stack in enterprise distributed systems by carving out a small portion of responsibility while offering a few basic guarantees with regard to state, synchronicity, awareness, and security.

Aurae brings enterprise identity as low as the socket layer in a system, which unlocks multi tenant workloads that run below tools like Kubernetes.

### Workloads 

 - Executables (Regular executable processes on a host system. Similar to [Systemd Units with ExecStart](https://www.freedesktop.org/software/systemd/man/systemd.service.html)).
 - Containers (A secure and opinionated container runtime is baked directly into the Aurae binary).
 - Virtualization (A secure and opinionated hypervisor is baked directly into the Aurae binary).






Use this repository to:
- develop against the suite.
- install the project toolchain into various Linux distributions.

If you are working directly with the aurae toolchain, or its source code you should probably start here.

## Installation

Currently the Aurae project is in alpha status and as such we do not yet support
package installations. Installation is done by installing the pre-requisites
and then compiling the project using the `rust` programming language.

### Dependencies

The Aurae environment depends on the `protoc` protocol buffer compiler being available within the path. 
Install `protoc` using your operating system's package manager (Or from source if you want to :) )
If you are running Ubuntu you can run the following,
```bash
sudo apt install -y protobuf-compiler
```

### Aurae Components

To install all Aurae components on a Linux distribution, run the following 
commands from within this repository:

```bash
make submodules # Please do not forget to do this!

# Then just follow a normal process
make 
make pki config # Generate certs and a default aurae config
make            # Compile and install aurae and auraed
```

Note that if you would like to do all of the above commands in one go you can also
run,
```bash 
make all
```

# Workflow

Open multiple tabs, or a tmux session, and in one start `auraed`,

```bash 
make start
```

In the other tab, you can then interact with `aurae` cli and `./scripts/`.

