# Colorful zsh

macOS Catalina부터 기본 터미널이 된 zsh를 더 편하게 보기 위한 개인적인 기록.

최대한 순정을 지향하기에 과한 튜닝을 싫어한다. 추가로 설치해야하는 프로그램들은 더더욱 싫어하고.

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
alias ls='ls -G -a'
alias ll='ls -G -al'
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
나는 bsd 순정값을 따라가겠다.

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

bold체도 사용 가능하다
```
%B	여기서부터 bold 지정
%b	여기서부터 bold 해제
```

