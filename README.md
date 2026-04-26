# test-repo

🚀 8600G Proxmox Server: Universal GitHub Runner & Python Lab
본 저장소는 AMD Ryzen 8600G(6C/12T) Proxmox LXC 환경을 GitHub Actions의 연산 노드로 활용하기 위한 구축 가이드와 실습 환경 설정을 포함합니다.

1. 개요 (Infrastructure)
Host: AMD Ryzen 5 8600G 

Virtualization: Proxmox VE (LXC Container)

OS: Ubuntu 24.04 LTS

Purpose: 로컬 서버 자원을 활용한 범용 파이썬 연산 및 CI/CD 자동화 인프라 구축

2. 시스템 준비 및 보안 설정
GitHub Runner는 보안을 위해 root 계정 실행을 금지합니다. 따라서 전용 일반 사용자 계정을 생성하고 필수 의존성을 설치합니다.

Bash
# 1. 전용 사용자 생성 및 권한 부여
sudo adduser github-runner
sudo usermod -aG sudo github-runner

# 2. 필수 의존성 패키지 설치
# Ubuntu에서는 perl-Digest-SHA 대신 libdigest-sha-perl를 사용합니다.
sudo apt update
sudo apt install -y libdigest-sha-perl build-essential curl git
