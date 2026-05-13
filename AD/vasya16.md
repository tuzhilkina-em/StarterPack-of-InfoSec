## Лабораторная - включение метода репликации по уведомлению для межсайтовых линков

### Подготовка инфраструктуры
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Развернутая инфраструктура описана [здесь](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/07054f12bf7fb9b368d04c6364035f5456eee718/AD/vasya13.md), на втором dcшнике (winlab.adlab.local) предустановлено 2 сетевых интерфейса, один из которых находится в той же подсети, что и корневой домен (10.0.0.10/24), второй интерфейс настроила на другую подсеть - 10.0.1.10/24

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; После этого нужно создать сайты для обеих подсеток: можно конечно делать через оснастку Active Directory Sites and Services, либо же через powershell. В первом интерфейсе уже создан дефолтный сайт, его надо переименовать, а после - создать сайт для второго сетевого интерфейса

![переименование дефолтного сайта](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/1bf9024a53db50b5f222a4189dea45a59b986f55/soc/L1/base/images/photo_2026-05-13%2016.29.33.jpeg)

После переименования деволтного сайта создаем сайт для дочки: 

![Создание второго сайта](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/365f8cf7e88d95653001d4d149f64501596fa081/soc/L1/base/images/photo_2026-05-13%2017.01.52.jpeg)


