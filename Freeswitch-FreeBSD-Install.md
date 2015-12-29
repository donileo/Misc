FREEBSD - Freeswitch 1.7 Installation
12/28/15

git clone https://freeswitch.org/stash/scm/fs/freeswitch.git

./boostrap.sh

./configure

edit modules.conf to specify what modules you want to build freeswitch with then save..

gmake

========
#####mod_shout -  If mod shout enabled in modules.conf
* make sure to have libmpg123 installed and lame installed as well via cd /usr/ports/audio/lame/ then gmake install
* edit freeswitch/src/mod/formats/mod_shout/MakeFile and change:
```
am__append_2 = -I/usr/include/lame
to
am__append_2 = -I/usr/local/include/lame
```
=========

edit freeswitch/src/mod/endpoints/mod_verto/ws.h line 
```
if defined(_MSC_VER) || defined(__APPLE__)
to
if defined(_MSC_VER) || defined(__APPLE__) || defined(__FreeBSD__)
```

then cd freeswitch/src/libs/spandsp/

automake --add-missing

cd back to freeswitch src dir

then gmake and see if there any compilation errors..

finally run: gmake install
