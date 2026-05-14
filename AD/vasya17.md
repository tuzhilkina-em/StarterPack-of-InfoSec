## Методы быстрого применения гпошек

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Развернутая инфраструктура описана [здесь](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/07054f12bf7fb9b368d04c6364035f5456eee718/AD/vasya13.md). На обоих dc уже созданы ou на 1000 пользователей каждый. Создаем новую гпошку и сразу назначаем на organizational unit:  
> New-GPO -Name "LAB-GPO"  
> New-GPLink -Name "LAB-GPO" -Target "OU=LabUsers,DC=adlab,DC=local"

 
![add-gpo](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/59a0d6dd91dcc9dfb0f217ef2852c4a43c32d8b4/soc/L1/base/images/photo_2026-05-14%2010.47.44.jpeg)  

Аналогично для OU=WinlabUsers:

![add-gpo](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/fabcfdd725a9f38817663966a0f1dd9fd5ce4245/soc/L1/base/images/photo_2026-05-14%2010.54.43.jpeg)  

В принципе, уже можно открывать gpmc.msc и редачить гпо как душе угодно

![gpmc](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/fabcfdd725a9f38817663966a0f1dd9fd5ce4245/soc/L1/base/images/photo_2026-05-14%2010.54.43.jpeg)
