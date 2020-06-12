# Belajar KVM

Saat ini teknologi `infrastruktur komputasi awan` atau sering disebut `cloud` sudah sangat matang, lalu untuk apa belajar teknologi virtualisasi?

Meskipun teknologi cloud sudah sedemikian hebat, namun untuk menjadi pengembang teknologi cloud dibutuhkan pengetahuan dasar teknologi virtualisasi.

Materi ini ditujukan bagi yang ingin mempelajari teknologi komputasi awan, sebagai prasyarat untuk mempelajari teknologi komputasi awan.

## Pengantar

Kebutuhan:

* Laptop/PC dengan spesifikasi ram minimal 4 GB
* OS Linux Ubuntu/Fedora

Cek:

```
# lscpu | grep Virtualization
Virtualization:        VT-x
```

## Install

`# yum install qemu-kvm libvirt libvirt-python libguestfs-tools virt-install`

## Start/Stop Service

```
# systemctl enable libvirtd
# systemctl start libvirtd
```

## Create VM

```
virt-install \
--virt-type=kvm \
--name centos7 \
--ram 2056 \
--vcpus=2 \
--os-variant=centos7.0 \
--cdrom=/var/lib/libvirt/boot/CentOS-7-x86_64-Minimal-1908.iso \
--network=bridge=ovs-br0,model=virtio \
--network=bridge=ovs-br1,model=virtio \
--graphics vnc \
--disk path=/var/lib/libvirt/images/centos7-min.qcow2,size=20,bus=virtio,format=qcow2
```
