# dcgm-exporter
Builded binary file from https://github.com/NVIDIA/dcgm-exporter

# Make Sure Cuda 12.x already installed
```
nvidia-smi
```

# Install Nvidia DCGM
```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2404/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt-get update

sudo apt-get install --yes --install-recommends datacenter-gpu-manager-4-cuda12
```

# Check Service DCGM
```
sudo systemctl enable nvidia-dcgm.service
sudo systemctl restart nvidia-dcgm.service
sudo systemctl status nvidia-dcgm.service

dcgmi discovery -l
```

# Install DCGM Exporter From Binary File
```
git clone https://github.com/AvnanRahman/dcgm-exporter.git
cd dcgm-exporter

sudo cp dcgm-exporter.service /etc/systemd/system/

sudo install -m 755 dcgm-exporter /usr/bin/dcgm-exporter

sudo install -m 644 -D default-counters.csv /etc/dcgm-exporter/default-counters.csv
```

# Enable & Start DCGM Exporter
```
sudo systemctl enable dcgm-exporter.service
sudo systemctl restart dcgm-exporter.service
sudo systemctl status dcgm-exporter.service
```