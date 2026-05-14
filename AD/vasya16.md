## Лабораторная - включение метода репликации по уведомлению для межсайтовых линков

### Подготовка инфраструктуры
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Развернутая инфраструктура описана [здесь](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/07054f12bf7fb9b368d04c6364035f5456eee718/AD/vasya13.md), на втором dcшнике (winlab.adlab.local) предустановлено 2 сетевых интерфейса, один из которых находится в той же подсети, что и корневой домен (10.0.0.10/24), второй интерфейс настроила на другую подсеть - 10.0.1.10/24

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; После этого нужно создать сайты для обеих подсеток: можно конечно делать через оснастку Active Directory Sites and Services, либо же через powershell. В первом интерфейсе уже создан дефолтный сайт, его надо переименовать, а после - создать сайт для второго сетевого интерфейса. Делать это следует с корневого домена тк роль Enterprise Admin существует именно там

![переименование дефолтного сайта](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/1bf9024a53db50b5f222a4189dea45a59b986f55/soc/L1/base/images/photo_2026-05-13%2016.29.33.jpeg)



После переименования дефолтного сайта создаем сайт для дочки: 

![Создание второго сайта](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/365f8cf7e88d95653001d4d149f64501596fa081/soc/L1/base/images/photo_2026-05-13%2017.01.52.jpeg)  



Далее займемся subnet mapping:

![subnet mapping](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/64092d2439da1be19b95b723c8577a0b3991d190/soc/L1/base/images/photo_2026-05-13%2017.01.54.jpeg)



ПроверОчка, уже на дочке  

![check](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/b765c5b07c3dc41d2aaac8533833ec032fefaed6/soc/L1/base/images/photo_2026-05-13%2017.01.58.jpeg)



Сами сайты готовы, отображаемые параметры при просмотре линков с DC 

![links](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/3c519b9ad6a4e193fd2afa8153fe47206407e16c/soc/L1/base/images/photo_2026-05-13%2017.27.15.jpeg)  



Изменение параметров межсайтовой репликации: (Последним ключом возможно указание любого параметра, после чего требуется указать новое значение)

![change](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/90fc05d29821eb0e5d125e773a0d84380a2fbfc9/soc/L1/base/images/photo_2026-05-14%2010.26.20.jpeg)   








