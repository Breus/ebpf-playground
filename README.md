# ebpf-playground
Playground for playing with eBPF

This README guides you to set-up eBPF with Go on MacOS

## Steps to set-up eBPF on MacOS

1. Install lima to have a Linux VM (more importantly, kernel): `brew install limactl`
2. Start lima with the ebpf-hello VM config: `limactl start hello-ebpf.yaml --mount-writable` 
3. Shell into the VM: `limactl shell hello-ebpf`


At the end, make sure to stop the VM again using: `limactl stop hello-ebpf` 
Alternatively, if you don't want to use the VM later again, use: `limactl delete hello-ebpf` 

## Useful links
- [Getting Statrted with eBPF in Go](https://ebpf-go.dev/guides/getting-started/)
- [Go library to read, modify and load eBPF programs](https://github.com/cilium/ebpf)
