Лабораторная работа №1 
 
1. Скачайте библиотеку boost с помощью утилиты wget. 
 
wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz 
 
2. Разархивируйте скаченный файл в директорию ~/boost_1_69_0. 
 
tar -xvf boost_1_69_0.tar.gz 
 
3. Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории. 
 
tree -L 1 
 
<img width="345" alt="image" src="https://github.com/esp1on/lab_01/assets/112684049/f4fce7f1-006b-4556-918e-5f669ef98698"> 
 
_6 директорий и 12 файлов_ 
 
4. Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории. 
 
tree 
 
_5637 директорий и 61191 файлов_ 
 
5 Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp). 
 
Для заголовочных файлов .h и .hpp, получим: find . -name "*.h" -o -name "*.hpp" | wc -l 
 
<img width="346" alt="image" src="https://github.com/esp1on/lab_01/assets/112684049/9a66d69e-9195-4166-ad8a-0ab6f029119d">
 
_15208_ 
 
Для файлов с расширением .cpp получим: find . -name "*.cpp" | wc -l 
 
<img width="345" alt="image" src="https://github.com/esp1on/lab_01/assets/112684049/fc4acee6-85ff-4dfe-850d-cbd7285c862d"> 
 
_13774_ 
 
Для остальных файлов получим: find . -not -name "*.h" -not -name "*.hpp" -not -name "*.cpp" | wc -l 
 
<img width="407" alt="image" src="https://github.com/esp1on/lab_01/assets/112684049/767e8ea4-d681-47ca-8d95-b426a90908d4"> 
 
_37847_ 
 
6. Найдите полный пусть до файла any.hpp внутри библиотеки boost. 
 
Перешел в директорию boost: cd boost 
 
Затем с помощью команды readlink -f any.hpp получим: _/mnt/c/Users/chean/boost_1_69_0/boost/any.hpp_ 
 
<img width="379" alt="image" src="https://github.com/esp1on/lab_01/assets/112684049/50716f56-5024-4abe-abfa-8cac81d2a845"> 
 
7 Выведите в консоль все файлы, где упоминается последовательность boost::asio. 
 
С помощью команды grep получим: grep -rl "boost:asio" 
 
8 Скомпилирутйе boost. 
 
Перейдем в директорию: cd boost_1_69_0/tools/build 
 
Запустим файл bootstrap.sh: sh bootstrap.sh 
 
Создадим файл куда установим bootstrap: mkdir output 
 
Установим bootstrap: ./b2 install --prefix=output 
 
9 Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs. 
 
mv output boost-libs 
 
10 Подсчитайте сколько занимает дискового пространства каждый файл в этой директории. 
 
Перейдем в директорию: cd boost_1_69_0/tools/build/boost-libs 
 
Найдем размер каждого файла: du -a 
 
11 Найдите топ10 самых "тяжёлых". 
 
Воспользуемся предыдущей командой, но также добавим команду sort по числовому значению du -a | sort -n и возьмем первые 10: 
 
<img width="322" alt="image" src="https://user-images.githubusercontent.com/126329578/221974217-c19057ec-52c8-4279-95e1-2bc1409aab22.png">
