# Отчёт по lab11

## Tutorial

1. Переходим в домашнюю директорию, создаём необходимые директории и переменные

_cd ~<br/>
mkdir install<br/>
mkdir tmp<br/>
export HOME_PREFIX=`pwd`/install<br/>
echo $HOME_PREFIX<br/>
export USERNAME=`whoami`_

2. Переходим во временную папку tmp

_cd tmp_

3. Скачиваем и устанавливаем libevent

_wget https://github.com/libevent/libevent/releases/download/release-2.1.8-stable/libevent-2.1.8-stable.tar.gz_

![wget](https://github.com/Dan10022002/lab11/blob/main/wget.png)

_tar -xvzf libevent-2.1.8-stable.tar.gz_

![tar](https://github.com/Dan10022002/lab11/blob/main/tar.png)

_cd libevent-2.1.8-stable_
_./configure --prefix=${HOME_PREFIX}_

![config](https://github.com/Dan10022002/lab11/blob/main/config.png)

_make && make install_

![install](https://github.com/Dan10022002/lab11/blob/main/install.png)

_cd .._

4. Скачиваем и устанавливаем ncurses

_wget http://invisible-island.net/datafiles/release/ncurses.tar.gz_

![wget2](https://github.com/Dan10022002/lab11/blob/main/wget2.png)

_tar -xvzf ncurses.tar.gz_

![tar2](https://github.com/Dan10022002/lab11/blob/main/tar2.png)

_cd ncurses-6.2_
_./configure --prefix=${HOME_PREFIX}_

![config2](https://github.com/Dan10022002/lab11/blob/main/config2.png)

_make && make install_

![install2](https://github.com/Dan10022002/lab11/blob/main/install2.png)

_cd .._

5. Скачиваем и устанавливаем tmux

_wget https://github.com/tmux/tmux/releases/download/2.5/tmux-2.5.tar.gz_

![wget3](https://github.com/Dan10022002/lab11/blob/main/wget3.png)

_tar -xvzf tmux-2.5.tar.gz_

![tar3](https://github.com/Dan10022002/lab11/blob/main/tar3.png)

_cd tmux-2.5_
_./configure --prefix=${HOME_PREFIX} CFLAGS="-I${HOME_PREFIX}/include -I${HOME_PREFIX}/include/ncurses" LDFLAGS="-L${HOME_PREFIX}/lib"_

![config3](https://github.com/Dan10022002/lab11/blob/main/config3.png)

_make && make install_

![install3](https://github.com/Dan10022002/lab11/blob/main/install3.png)

_cd .._ 

6. Скачиваем и устанавливаем ngrok

_wget https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip_

![wget4](https://github.com/Dan10022002/lab11/blob/main/wget4.png)

_unzip ngrok-stable-linux-amd64.zip<br/>
mv ngrok ${HOME_PREFIX}/bin_

7. Задаём необходимые переменные и запускаем tmux

_export LD_LIBRARY_PATH=${HOME_PREFIX}/lib<br/>
export PATH="${HOME_PREFIX}/bin:${PATH}"<br/>
tmux_

8. Удаляем временные папку и папку куда скачивались необходимые файл для программ

_cd ~<br/>
rm -rf tmp install_

9. Создаём сеанс совместной разработки

_tmux new -s session_with_group_

10.Создаём "тонель" для установки соединения(#Alisa)

_open https://ngrok.com/signup<br/>
export NGROK_TOKEN=1tMnIwGYbZ5XQli9CwugDQAL0lK_5THsiYVNwVaiofH6WuQYD<br/>
ngrok authtoken ${NGROK_TOKEN}<br/>
ngrok tcp 22_

![ngrok](https://github.com/Dan10022002/lab11/blob/main/ngrok.png)
