# Linux-Commands
Linux / Bash командалық жол анықтамалығы

Автор: Per1zat  
Құрылған күні: 20.12.2025

# Bash бойынша шпаргалка

### Өз командаларыңызды және пайдалы материалдарды `Pull Request` арқылы қосыңыз.

Бұл репозиторий Git Bash, macOS (OSX) терминалы және Linux үшін негізгі командалар анықтамалығын қамтиды.

## Мәні

Командалық жол — операциялық жүйені басқарудың ыңғайлы әрі жоғары тиімді құралы. Пайдаланушы командаларды мәтін түрінде енгізіп, орындалу нәтижесін немесе қате туралы хабарламаны (себебі көрсетілген) алады.

Консольмен жұмыс істегенде пайдаланушы әрқашан белгілі бір директорияда болады, оның жолы курсордың алдындағы шақыру жолында көрсетіледі.  

Егер `~` таңбасы көрсетілсе, бұл ағымдағы директория пайдаланушының үй директориясы екенін білдіреді (Windows-та көбіне: `C:/Users/ПАЙДАЛАНУШЫ_АТЫ/`).  

Егер `/d/projects` сияқты жол көрсетілсе, белсенді директория `D:/projects` болады.

## Файлдық жүйе

### Қапшық мазмұнын қарау

```bash
pwd                     # ағымдағы жолды көрсету (PRINT WORK DIRECTORY қысқартуы)
ls                      # қапшық мазмұнын көрсету
ls -l                   # файлдар мен қапшықтар туралы кеңейтілген ақпарат көрсету
ls -a                   # жасырын файлдар мен қапшықтарды да көрсету
ls -a -1                # дәл сол, бірақ бір бағанға шығару
ls -hF -1 --sort=extension # қапшық мазмұнын «әдемі, бір бағанмен» көрсету
ls build/css            # АҒЫМДАҒЫ_ҚАПШЫҚ/build/css қапшығының мазмұнын көрсету
ls /d/projects          # D:/projects қапшығының мазмұнын көрсету
Файлдық жүйеде жылжу
Пайдаланушы әрқашан қандай да бір қапшықта болады, ол (немесе толық жолы) команда енгізу аймағына дейін көрсетіледі.
cd projects             # ағымдағы қапшықтағы projects қапшығына өту
cd /d/projects          # windows: D:/projects мекенжайындағы projects қапшығына өту
cd /c/Program\ Files    # windows: C:/Program Files қапшығына өту
cd .                    # ағымдағы директория
cd ..                   # ата-аналық қапшыққа өту
cd ~                    # үй директориясы
cd -                    # соңғы жұмыс қапшығына өту
Қапшық атауын толық термеу үшін алғашқы бірнеше әріпті теріп, <kbd>Tab</kbd> басыңыз — автотолықтыру іске асады. Бұл кез келген командаға қатысты.
Қапшықтар мен файлдар жасау
mkdir project                        # «project» атты қапшық жасау
mkdir project project/css project/js # бірнеше қапшық жасау
mkdir -p project/{css,js}            # жоғарыдағыдай

touch index.html                     # файл жасау
touch index.html css/style.css js/script.js # файлдар жасау (css/ және js/ қапшықтары бар болуы керек)
Файлдарды көшіру
cp index.html catalog.html # index.html файлын сол каталогта catalog.html деп көшіру
cp index.html old/         # index.html файлын old/ қапшығына көшіру
cp temp/ temp2/ -r         # каталогты көшіру (дублирлеу)
Файлдарды қайта атау немесе жылжыту
mv index.html old              # файлды қапшыққа жылжыту
mv index.html old/new_name.txt # файлды қапшыққа жаңа атаумен жылжыту
mv order.txt orderNew.txt      # файл атауын өзгерту
Қапшықтар мен файлдарды жою
rm ghost.png             # файлды жою
rm -rf old               # қапшықты ішіндегісімен қоса жою
Алиастар
Командалар үшін алиастар (балама атаулар) жасауға болады.
Ол үшін пайдаланушы қапшығындағы (OSX және linux) немесе C:/Users/ПАЙДАЛАНУШЫ_АТЫ/.bashrc (Windows) файлына alias pro='cd /d/projects' сияқты жолдар жазылады (бір жол — бір алиас).
alias                 # жүйеде бар алиастарды көрсету
alias c='clear'       # консольді тазалайтын алиас жасау
unalias c             # "c" алиасын жою
unalias -a            # барлық алиастарды жою
Әртүрлі
GUI-ге қарағанда консольмен жылдамырақ жұмыс істеуге мүмкіндік беретін немесе жай ғана ыңғайлы командалар топтамасы.
clear                 # консольді тазалау
df -h                 # дискідегі орын қолдану статистикасын көрсету
grep -i -n --color 'carousel' index.html css/style.css # екі файлдан carousel сөзін табу (регистрді елемеу)
grep word -r project  # project қапшығындағы барлық файлдардан word сөзін табу
find . -iname '*ind*' # ағымдағы қапшықтан ind бар атауларды табу
ls -a >> file.txt     # ls -a нәтижесін file.txt файлына жазу
ls src/less/mixins    # көрсетілген жолдағы қапшық мазмұнын көру
echo  "Some text"     # мәтінді консольге шығару
chmod +x ./fileName   # файлды орындалатын ету
whoami                # пайдаланушы атын көрсету
Айнымалыларды пайдалану
Айнымалылар сценарий файлында ақпарат сақтауға мүмкіндік береді.
Айнымалылардың екі түрі бар:

Орта айнымалылары
echo $HOME
echo "Env variable $HOME"
Пайдаланушы айнымалылары
#!/bin/zsh

grade=5 
person="Adam"
echo "$person is a good boy, he is in grade $grade"
Командаларды айнымалыға жазу
Команда шығуын айнымалыға сақтауға болады.
mydir=`pwd`
mydir=$(pwd)
Мысал скрипт:
#!/bin/bash

mydir=$(pwd)
echo $mydir
Математикалық операциялар
var1=$(( 5 + 5 ))
echo $var1

var2=$(( $var1 * 2 ))
echo $var2
if-then конструкциясы
if команда
then
командалар
fi
Мысал:
#!/bin/bash
if pwd
then
echo "It works"
fi
if-then-else
if команда
then
командалар
else
командалар
fi
#!/bin/bash

user=anotherUser
if grep $user /etc/passwd
then
echo "The user $user Exists"
else
echo "The user $user doesn’t exist"
fi
CASE конструкциясы
case "$extension" in
  "jpg"|"jpeg") echo "It's image with jpeg extension." ;;
  "png")        echo "It's image with png extension."  ;;
  "gif")        echo "Oh, it's a giphy!"               ;;
  *)            echo "Woops! It's not image!"          ;;
esac
Циклдер
Bash-та төрт цикл бар: for, while, until, select.
FOR
for arg in elem1 elem2 ... elemN
do
  # командалар
done
WHILE — шарт ақиқат болғанша орындалады
while [[ condition ]]
do
  # командалар
done
UNTIL — шарт жалған болғанша орындалады
until [[ condition ]]; do
  # командалар
done
SELECT — пайдаланушы мәзірі үшін
select answer in elem1 elem2 ... elemN
do
  # командалар
done
Сандарды салыстыру
n1 -eq n2 # тең
n1 -ge n2 # үлкен немесе тең
n1 -gt n2 # үлкен
n1 -le n2 # кіші немесе тең
n1 -lt n2 # кіші
n1 -ne n2 # тең емес
Жолдарды салыстыру
str1 = str2
str1 != str2
str1 \< str2
str1 \> str2
-n str1
-z str1
Файлдарды тексеру
-d file
-e file
-f file
-r file
-s file
-w file
-x file
Операторлар
command1 | command2     # pipe
command1 ; command2     # кезекпен орындау
command1 && command2    # бірінші сәтті болса
command1 || command2    # бірінші сәтсіз болса
Тесттік жақшалар:
if [[ 1 -eq 1 ]]; then echo "true"; fi
