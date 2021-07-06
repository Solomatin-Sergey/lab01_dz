# lab01_dz

> 1.Скачайте библиотеку boost с помощью утилиты wget. Адрес для скачивания https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz.

wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz

> 2.Разархивируйте скаченный файл в директорию ~/boost_1_69_0

tar -xf boost_1_69_0.tar.gz

> 3.Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.

find . -maxdepth 1|wc
на выходе: 19 19 209
// -maxdepth - максимальная глубина поиска (в данном случае текущая директория)
// 19 - это включая саму директорию, поэтому всего 18.

> 4.Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.

find ./ |wc

> 5.Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).

find ./ -name ".h" |wc
find ./ -name ".cpp" |wc
ind ./ -not -name ".h" -not -name ".cpp"|wc

> 6.Найдите полный пусть до файла any.hpp внутри библиотеки boost.

find ./ -name "any.hpp"

* ./boost/any.hpp
* ./boost/spirit/home/support/algorithm/any.hpp
* ./boost/proto/detail/any.hpp
* ./boost/hana/any.hpp
* ./boost/hana/fwd/any.hpp
* ./boost/xpressive/detail/utility/any.hpp
* ./boost/type_erasure/any.hpp
* ./boost/fusion/algorithm/query/any.hpp
* ./boost/fusion/algorithm/query/detail/any.hpp
* ./boost/fusion/include/any.hpp

> 7.Выведите в консоль все файлы, где упоминается последовательность boost::asio.

grep -r "boost::asio" ./

> 8.Скомпилирутйе boost. Можно воспользоваться инструкцией или ссылкой.

./bootstrap.sh --prefix=boost_output
./b2 install

> 9.Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.

mkdir ~/boost-libs
mv boost_output/ ~/boost-libs/

> 10.Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.

ls -Rgh

> 11.Найдите топ10 самых "тяжёлых".

find . -type f -exec ls -s {} ; | sort -n | head -10



