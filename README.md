# examtest-repo

8600G Proxmox Server: Universal GitHub Runner & Python Lab
본 저장소는 AMD Ryzen 8600G(6C/12T) Proxmox LXC 환경을 GitHub Actions의 연산 노드로 활용하기 위한 구축 가이드와 실습 환경 설정을 포함합니다.

-Host: AMD Ryzen 5 8600G (Radeon 760M iGPU 포함)

-Virtualization: Proxmox VE (LXC Container)

-OS: Ubuntu 24.04 LTS

-Purpose: 로컬 서버 자원을 활용한 범용 파이썬 연산 및 CI/CD 자동화 인프라 구축

# How to setup
### runner 생성
```
## 전용 사용자 생성&권한 부여
sudo adduser github-runner
 sudo usermod -aG sudo github-runner

## 계정 전환
 su - github-runner
 mkdir actions-runner && cd actions-runner

## 러너 다운로드 및 압축 해제 (버전은 최신으로 확인)
tar xzf ./actions-runner-linux-x64-2.x.x.tar.gz

## 러너 설정 (토큰 입력)
./config.sh --url https://github.com/[사용자명]/[레포명] --token [TOKEN]

## 백그라운드 서비스 등록 (상시 가동)
sudo ./svc.sh install
sudo ./svc.sh start
```
### 실습환경 구축
```

```




