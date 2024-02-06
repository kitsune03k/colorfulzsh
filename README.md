# Colorful zsh

<img src="https://raw.githubusercontent.com/kitsune03k/colorfulzsh/main/resource/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202023-12-30%20%EC%98%A4%ED%9B%84%202.47.19.png">

macOS Catalina부터 기본 터미널이 된 zsh를 더 편하게 보기 위한 개인적인 기록.

<img src="https://raw.githubusercontent.com/kitsune03k/colorfulzsh/main/resource/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202023-12-30%20%EC%98%A4%ED%9B%84%202.47.59.png">

진행 이전에 터미널 앱의 기본 설정은 이렇다.

최대한 순정을 지향하기에 과한 튜닝을 싫어한다. 추가로 설치해야하는 프로그램들은 더더욱 싫어하고.

타 os의 향만 적당히 첨가한 수준으로만 만들것이다.

혹시나 필자의 미적감각과 비슷하여 마음에 들어 이를 따라하고 싶다면 이후부터 일련의 모든 과정이 참 귀찮으므로 

그냥 올린 .zshrc, .vimrc를 홈 폴더에 받아서 쓰는것을 추천한다.

#

### 1. ~/.zshrc
사용자의 홈폴더에 zshrc 파일을 만들어야한다.

```
vi ~/.zshrc
```
zsh에서 색상을 켜준다. 

```
export CLICOLOR=1
```

### 2. ls
ls시 색상을 표시하게 한다.
```
alias ls='ls -G'
alias ll='ls -G -l'
alias la='ls -G -a'
alias lal='ls -G -al'
```
<img src="https://raw.githubusercontent.com/kitsune03k/colorfulzsh/main/resource/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202023-12-30%20%EC%98%A4%EC%A0%84%2010.42.48.png">

사실 -G 옵션은 ls에 원래 존재하기에, 위의 줄은 ls 입력마다 ls -G로 대체해주는 것일 뿐이다.

ls시 색상 지정은 아래와 같이 가능하다.
```
export LSCOLORS=...
```

...에는 foreground(글자), background(배경) 하나씩 하여 총 11개의 쌍, 22개의 char이 온다.

순서대로 아래와 같다.
```
1.   directory
2.   symbolic link
3.   socket
4.   pipe
5.   executable
6.   block special
7.   character special
8.   executable with setuid bit set
9.   executable with setgid bit set
10.  directory writable to others, with sticky bit
11.  directory writable to others, without sticky bit
```
색상으로는 다음과 같다.

```
a	검은색
b	빨간색
c	초록색
d	갈색(사실상 노란색임)
e	파란색
f	마젠타색
g	시안색
h	회색
```

대문자는 bold체 이다.
```
A	bold black, usually shows up as dark grey
B	bold red
C	bold green
D	bold brown, usually shows up as yellow
E	bold blue
F	bold magenta
G	bold cyan
H	bold light grey; looks like bright white
```
단, 파일은 기본색상으로 표시된다.

```
x	default foreground or background
```
아무 색상도 적용하지 않은 기본값은 x이다.

출처 : [https://gist.github.com/thomd/7667642](https://gist.github.com/thomd/7667642)

<img src="https://raw.githubusercontent.com/kitsune03k/colorfulzsh/main/resource/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202023-12-30%20%EC%98%A4%EC%A0%84%2011.40.54.png">

순서대로 ax...(검은색 바탕이라 글자 안나옴), bx..., ..., hx...이다

```
export LSCOLORS=exfxcxdxbxegedabagacad
```
필자는 bsd 순정값을 따라가겠다.

### 3. username & cwd
```
export PROMPT='...'

```

<img src="https://raw.githubusercontent.com/kitsune03k/colorfulzsh/main/resource/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202023-12-30%20%EC%98%A4%ED%9B%84%2012.27.46.png">

macOS 터미널의 순정 상태는 아마 이럴것이다.

위 사진이 의미하는 바는 아래와 같다.

```
%n	$USERNAME
$m	The hostname up to the first ‘.’
%1	Current working directory. If an integer follows the ‘%’, it specifies a number of trailing components of the current working directory to show
%#	A ‘#’ if the shell is running with privileges, a ‘%’ if not.
```

참고 : [https://zsh.sourceforge.io/Doc/Release/Prompt-Expansion.html](https://zsh.sourceforge.io/Doc/Release/Prompt-Expansion.html)

색상의 지정과 초기화는 원하는곳에 아래를 적당히 이용한다.
```
%F{색상명}	여기서부터 foreground 색상 지정
%f{색상명}	여기서부터 foreground 색상 초기화
%K{색상명}	여기서부터 background 색상 지정
%k{색상명}	여기서부터 background 색상 초기화
```
색상은 문자로도 입력 가능하나

```
000	black
001	red
002	green
003	yellow
004	blue
005	magenta
006	cyan
007	white
```

<img src="https://raw.githubusercontent.com/kitsune03k/colorfulzsh/1a3643a9cde2563d9c4a4cbd4d8d3dd17ce2c22f/resource/Xterm_256color_chart.svg">

source : [https://gist.github.com/jasonm23/2868981](https://gist.github.com/jasonm23/2868981)

<img src="https://raw.githubusercontent.com/kitsune03k/colorfulzsh/main/resource/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202023-12-30%20%EC%98%A4%ED%9B%84%202.20.11.png">

터미널 옵션에서 xterm-256색상을 선택하고 위의 숫자로 입력하면 더 많은 색상을 선택할 수 있다.

bold체도 사용 가능하다.
```
%B	여기서부터 bold 지정
%b	여기서부터 bold 해제
```

<img src="https://raw.githubusercontent.com/kitsune03k/colorfulzsh/main/resource/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202023-12-30%20%EC%98%A4%ED%9B%84%202.36.20.png">

필자는 무난하게 우분투에서 쓰던 색상, 구성으로 적용했다.

### 4. 적용
여기까지 완성되었으면 .zshrc 파일을 저장하고
```
source ~/.zshrc
```
를 실행해주면 바로 적용이 된다.

### 5. Vim
조금 다른 얘기지만 하는김에 Vim 에디터에도 컬러를 입혀보고자 한다.

macOS는 순정으로 Vim을 포함하고있으나, 우분투에서 쓰던 것 처럼 색상이 자동으로 입혀지지 않는다.

~/.vimrc에
```
syntax on
```
을 추가하면

<img src="https://raw.githubusercontent.com/kitsune03k/colorfulzsh/main/resource/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202023-12-30%20%EC%98%A4%ED%9B%84%202.52.14.png">

문법에 맞춰 색이 입혀지지만, 색상이 영 가독성이 좋지가 못하다. 

이 입혀지는 색상을 Vim에서 colorscheme라 하는데
```
blue
darkblue
default
delek
desert
elflord
evening
habamax
industry
koehler
lunaperche
morning
murphy
pablo
peachpuff
quiet
retrobox
ron
shine
slate
sorbet
torte
wildcharm
zaibatsu
zellner
```
macOS Vim은 순정으로 위와같은 colorscheme를 가지고 있다.

```
colorscheme default
```

<img src="https://raw.githubusercontent.com/kitsune03k/colorfulzsh/main/resource/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202023-12-30%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%208.04.19.png">

필자는 우분투에서 쓰던 익숙한 느낌이 좋아서 이를 default로 지정해주었다.

위의 색상 스키마가 전부 마음에 안든다면 "Vim Colorscheme"라 구글링하면 많이 나오니 마음에 드는것을 적용하면 된다.
