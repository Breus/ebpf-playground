# ebpf-playground
Playground for playing with eBPF

This README guides you to set-up eBPF with Go on MacOS

## Steps to set-up eBPF on MacOS

1. Install lima to have a Linux VM (more importantly, kernel): 
   ```bash
   brew install limactl
   ```
2. Start lima with the VM using `ebpf-playground.yaml` config:
   ```bash
   limactl start ebpf-playground.yaml --mount-writable
   ```
3. Shell into the VM: 
   ```bash
   limactl shell ebpf-playground
   ```
4. This repository contains the test eBPF program from the guide [Getting Started with eBPF in Go](https://ebpf-go.dev/guides/getting-started/):
   ```bash
   gen.go
   go.mod
   counter.c
   main.go
   ```
5. Build ebpf-playground module:
   ```bash
   go generate && go build
   ```
6. Run the ebpf-playground
   ```bash
   sudo ./ebpf-playground
   ```
7. Output:
   ```text
   2024/05/25 11:50:36 Counting incoming packets on eth0..
   2024/05/25 11:50:37 Received 2 packets
   2024/05/25 11:50:38 Received 3 packets
   2024/05/25 11:50:39 Received 4 packets
   ```
8. While `ebpf-playground` is attached you can do any network operation to see it being intercepted by it:
   ```bash
   curl https://google.com
   ```
   and you will see more packets being intercepted:
   ```text
   2024/05/25 11:50:40 Received 7 packets
   2024/05/25 11:50:41 Received 27 packets
   2024/05/25 11:50:42 Received 28 packets
   ```

## Cleanup
At the end, make sure to stop and remove the VM using: 
```bash
limactl stop ebpf-playground
limactl delete ebpf-playground
```

## Useful links
- [Getting Started with eBPF in Go](https://ebpf-go.dev/guides/getting-started/)
- [Go library to read, modify and load eBPF programs](https://github.com/cilium/ebpf)
