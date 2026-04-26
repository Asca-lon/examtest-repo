# examtest-repo

8600G Proxmox Server: Universal GitHub Runner & Python Lab
본 저장소는 AMD Ryzen 8600G(6C/12T) Proxmox LXC 환경을 GitHub Actions의 연산 노드로 활용하기 위한 구축 가이드와 실습 환경 설정을 포함합니다.

-Host: AMD Ryzen 5 8600G (Radeon 760M iGPU 포함)

-Virtualization: Proxmox VE (LXC Container)

-OS: Ubuntu 24.04 LTS

-Purpose: 로컬 서버 자원을 활용한 범용 파이썬 연산 및 CI/CD 자동화 인프라 구축

# How to setup
### runner 생성

``` bash
sudo adduser github-runner
sudo usermod -aG sudo github-runner

su - github-runner
mkdir actions-runner && cd actions-runner

tar xzf ./actions-runner-linux-x64-2.x.x.tar.gz

./config.sh --url https://github.com/[사용자명]/[레포명] --token [TOKEN]

sudo ./svc.sh install
sudo ./svc.sh start
```
### 실습환경 구축
``` bash
wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-x86_64.sh
bash Miniforge3-Linux-x86_64.sh

~/miniforge3/bin/conda init bash
source ~/.bashrc

conda create -n lab python=3.13 -y
conda activate lab
```

### Actions workflow 연동
```

```
``` YAML
name: 8600G Universal Compute

on: [push]

jobs:
  execute:
    runs-on: self-hosted  # 8600G 러너 지목
    steps:
      - uses: actions/checkout@v4
      
      - name: Run Lab Script
        run: |
          # lab 환경의 파이썬 절대 경로를 사용하여 실행
          /home/github-runner/miniforge3/envs/lab/bin/python main.py

```




