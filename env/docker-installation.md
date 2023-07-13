# 목록<!-- omit in toc -->
- [1. 공식문서](#1-공식문서)
- [2. 요구사항](#2-요구사항)
  - [2.1. 우분투 버전](#21-우분투-버전)
  - [2.2. 아키텍처](#22-아키텍처)
- [3. 설치](#3-설치)
  - [3.1. 이전 버전 제거](#31-이전-버전-제거)
  - [3.2. APT저장소 설정](#32-apt저장소-설정)
    - [3.2.1. 필요한 패키지 설치](#321-필요한-패키지-설치)
    - [3.2.2. 도커 GPG키 추가](#322-도커-gpg키-추가)
    - [3.2.3. APT저장소 설정](#323-apt저장소-설정)
  - [3.3. 도커엔진 설치](#33-도커엔진-설치)
    - [3.3.1. APT로 도커엔진 설치](#331-apt로-도커엔진-설치)
    - [3.3.2. sudo없이 사용하기](#332-sudo없이-사용하기)
    - [3.3.3. 테스트](#333-테스트)
- [4. 제거](#4-제거)
  - [4.1. 도커엔진 제거](#41-도커엔진-제거)
  - [4.2. 이미지, 컨테이너, 볼륨 삭제](#42-이미지-컨테이너-볼륨-삭제)
# 1. 공식문서
[Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
# 2. 요구사항
## 2.1. 우분투 버전
- Ubuntu Lunar 23.04
- Ubuntu Kinetic 22.10
- Ubuntu Jammy 22.04 (LTS)
- Ubuntu Focal 20.04 (LTS)
## 2.2. 아키텍처
- x86_64 (or amd64)
- armhf
- arm64
- s390x
# 3. 설치
## 3.1. 이전 버전 제거
```
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
```
## 3.2. APT저장소 설정
### 3.2.1. 필요한 패키지 설치
```
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
```
### 3.2.2. 도커 GPG키 추가
```
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```
### 3.2.3. APT저장소 설정
```
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
## 3.3. 도커엔진 설치
### 3.3.1. APT로 도커엔진 설치
```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
### 3.3.2. sudo없이 사용하기
```
sudo usermod -aG docker $USER
로그아웃 후 로그인
```
### 3.3.3. 테스트
```
docker run hello-world
docker version
docker compose version
```
# 4. 제거
## 4.1. 도커엔진 제거
```
sudo apt-get purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras
```
## 4.2. 이미지, 컨테이너, 볼륨 삭제
```
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
```