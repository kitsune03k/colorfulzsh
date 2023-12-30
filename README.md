# Colorful zsh

macOS의 기본 터미널인 zsh를 더 편하게 보기 위한 개인적인 기록.

순정을 지향해서 과한 튜닝은 최대한 삼가는 편이다.

### 1. ~/.zshrc
사용자의 홈폴더에 zshrc 파일을 만들어야한다.

```
vi .zshrc
```
zsh에서 색상을 켜준다. 

```
export CLICOLOR=1
```

### 2. ls
ls시 색상을 표시하게 한다.
```
alias ls='ls -G'
```
사실 -G 옵션은 ls에 원래 존재하기에, 위의 줄은 ls 입력마다 ls -G로 대체해주는 것일 뿐이다.

ls시 색상 지정은 아래와 같이 가능하다.
```
export LSCOLORS=...
```

...에는 foreground, background 하나씩 하여 총 11개의 쌍, 22개의 char이 온다.

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

아무 색상도 적용하지 않은 기본값은 x이다.
```
x	default foreground or background
```

출처 : [https://gist.github.com/thomd/7667642](https://gist.github.com/thomd/7667642)


나는 여러 고민끝에 아래와 같이 해주었다.
```

```

### 3. color