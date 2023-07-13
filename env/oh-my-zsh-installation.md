# 공식문서
- [Zsh](https://www.zsh.org/)
- [Oh My Zsh](https://ohmyz.sh/#install)
# 설치
## Zsh
```
sudo apt install -y zsh
chsh -s $(which zsh)
```
로그아웃 후 다시 로그인
## Oh My Zsh 설치
```
sudo apt install fonts-powerline
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
## 설정
### 테마
- `~/.zshrc` 수정
```
#ZSH_THEME="robbyrussell"
ZSH_THEME="agnoster"
```
### 플러그인
- 다운로드
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions
```
- `~/.zshrc` 수정
```
#plugins=(git)
plugins=(git zsh-syntax-highlighting zsh-autosuggestions)
```