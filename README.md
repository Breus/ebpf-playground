# ebpf-playground
Playground for playing with eBPF

This README guides you to set-up eBPF with Go on MacOS

## Steps to set-up eBPF on MacOS

1. Install lima to have a Linux VM (more importantly, kernel): `brew install limactl`
2. Start lima with the ebpf-hello VM config: `limactl start hello-ebpf.yaml --mount-writable` 
3. Shell into the VM: `limactl shell hello-ebpf` 

## Useful links

https://github.com/cilium/ebpf
