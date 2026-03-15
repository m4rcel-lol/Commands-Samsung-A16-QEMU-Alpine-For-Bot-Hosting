cat > ~/alpine/start.sh << 'EOF'
#!/data/data/com.termux/files/usr/bin/bash
qemu-system-aarch64 \
  -machine virt \
  -cpu cortex-a57 \
  -m 1024 -smp cpus=2 \
  -drive file=$HOME/alpine/alpine.qcow2,if=virtio \
  -cdrom $HOME/alpine/alpine-virt-3.20.2-aarch64.iso \
  -netdev user,id=n1,hostfwd=tcp::2222-:22 \
  -device virtio-net-device,netdev=n1 \
  -nographic
EOF
chmod +x ~/alpine/start.sh
~/alpine/start.sh
