# Zsh(Oh My Zsh) 세팅

> https://gist.github.com/kevin-smets/8568070
>
> https://nolboo.kim/blog/2015/08/21/oh-my-zsh/ 
>
> http://thdev.tech/mac/2016/05/01/Mac-ZSH-Install.html 를 참고하였습니다.
>
> mac os, iTerm2 기준으로 작성하였습니다.
>
> ubuntu를 비롯한 다른 os에서는 설치를 제외한 부분은 같으니 그 부분만 보시면 됩니다.
>
> updated 2018.01.17



## Install zsh with brew

```bash
brew update
brew install zsh
```

## Install with curl

```bash
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## Change shell

```bash
chsh -s `which zsh`
```

## Powerlevel9k

```bash
git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k
```

`.zshrc`에  `ZSH_THEME="powerlevel9k/powerlevel9k"`를 추가하면 된다.

## Colorscheme

[Solarized Dark theme](https://raw.githubusercontent.com/mbadolato/iTerm2-Color-Schemes/master/schemes/Solarized%20Dark%20-%20Patched.itermcolors) 여기서 theme을 다운 받는다.  그리고 iTerm → preferences → profiles → colors → load presets에서 적용한다.



## Font

```bash
# clone
git clone https://github.com/powerline/fonts.git --depth=1
# install
cd fonts
./install.sh
# clean-up a bit
cd ..
rm -rf fonts
```

[Meslo](https://github.com/powerline/fonts/blob/master/Meslo%20Slashed/Meslo%20LG%20M%20Regular%20for%20Powerline.ttf)에서 view raw로 font를 다운 받고 iTerm → Preferences → Profiles → Text → Change Font에서 `Meslo LG M DZ for Powerline`를 선택하면 된다.

> Meslo이면서 Powerline인 다른 것을 선택해도 되는 것 같다.

## Plugin

### Alias-tips

```bash
cd ${ZSH_CUSTOM1:-$ZSH/custom}/plugins
git clone https://github.com/djui/alias-tips.git
```

`.zshrc`에 다음과 같은 줄 추가

```bash
export ZSH_PLUGINS_ALIAS_TIPS_TEXT="Alias tip: "
```

```bash
vi ~/.zshrc
# -plugins=(...)
# +plugins=(... alias-tips)
```



### zsh-syntax-highlighting

> mac os가 아닌 경우 https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md 참고

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
echo "source ${(q-)PWD}/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc
```

현재 shell에서 작동하게 하려면

```bash
source ./zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

마찬가지로 `.zshrc`에 plugin에 `zsh-syntax-highlighting` 추가



---

> updated 2018.01.28

### python virtualenv 관련 세팅

현재 virtualenv를 activate하면 display가 되지 않음. 따라서 그걸 display 하려면 현재 `.zshrc`에 다음과 같이 코드를 추가하면 됨.

```bash
VIRTUAL_ENV_DISABLE_PROMPT=false
```
을 하거나 

```bash
POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(virtualenv context dir rbenv vcs)
```
를 하면 된다.
