## Лаба: ADMX Central Store
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ***ADMX Central Store*** - централизованное хранилище административных шаблонов Group Policy. Оно используется для того, чтобы все администраторы домена работали с единым набором ADMX/ADML-файлов при редактировании GPO. Административные шаблоны - это набор описаний политик Windows. Они определяют то, какие параметры доступны в Group Policy Editor, как они отображаются, какие registry keys изменяются и какие значения допустимы  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ADMX содержит описание политики, а ADML - языковые ресурсы и отображаемый текст. ADMX Central Store решает проблему рассинхронизации шаблонов. Вместо локального использования C:\Windows\PolicyDefinitions все GPMC начинают использовать единое доменное хранилище

[Гайд и справка о том, что это и как, я делала в соответствии с официальным руководством](https://learn.microsoft.com/ru-ru/troubleshoot/windows-client/group-policy/create-and-manage-central-store)  
<br>  

### 1. Подготовка инфраструктуры 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Я развернула на виртуалке следующую инфру: корневой домен-контроллер (adlab.local), на котором развернуты dns, ad ds, remote access, также отдельными машинами подянты dhcp-server, dhcp-fileover, второй домен-контроллер (winlab.adlab.local), который по отношению к первому является дочерним, на нем подняты dns и ad ds соответственно (про развернутый битрих и siem на базе elk будет отдельно позже). После установления сетевой связности компонентов и настройки их стабильной работы создала по 1000 пользователей отдельно, для чего на каждом DC был создан отдельный OU для удобства хранения и назначения gpo:  

> New-ADOrganizationalUnit -Name "WinlabUsers"  
<br>  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Далее создала переменную $password. В нее кладется пароль, преобразованный в тип SecureString. Командлет New-ADUser не принимает обычный текстовый пароль напрямую, поэтому строку "p@ssword!123" нужно преобразовать, тк это виртуалка с паролями можно куралесить напрямую:

> $password = ConvertTo-SecureString "p@ssword!123" -AsPlainText -Forse  
<br>  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Для обеих DС фигачим по 1000 пользаков командой ниже, атрибут **-Path** меняется в зависимости от структуры леса и относительного расположения домена

> 1..1000 | ForEachObject { NewADUser -Name "winlabUser$_" -SamAccountName "winlabUser$_" -UserPrincipalName "winlabUser$_adlab.local" -Path "OU=WinlabUsers,DC=adlab,DC=local" -AccountPassword $password -Enabled $true }
<br>

![создание пользаков](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/27b9956d8b6938cb0432951ee3e19805642dcff1/soc/L1/base/images/photo_2026-05-13%2015.08.15.jpeg)  

Вот что выйдет:  

![результат](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/e7ac9c8ce99e6c92df24fb19c70ed777d441f403/soc/L1/base/images/photo_2026-05-13%2015.08.18.jpeg)  




### 2. Просмотр содержимого каталога C:\\Windows\PolicyDrfinitions
Дальше процесс опишу только для дочернего домена, для корневого и прочих действия будут аналогичными. В Powershell, открытом от имени администратора перейдем в C:\\Windows\PolicyDefinitions и командой ls сможем увидеть хранимые там файлы  
<br>


### 3. Подготовка каталога и перенос файлов в единое хранилище
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Перейдем в каталог SYSVOL и оттуда в соответствие с руководством майкросовт создадим дублирующую папку:
> mkdir contoso.com\policies\PolicyDefinitions    

После чего необходимо скопировать содержимое в созданную директорию и не забыть переименовать старое хранилище:  

![перенос](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/74a91ce570b8dff3c8c265bf8d7c019f1465d7fa/soc/L1/base/images/photo_2026-05-13%2015.08.20.jpeg)

### PS: Это вообще зачем? 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Централизованное хранилище ADMX нужно для того, чтобы все администраторы домена использовали один и тот же набор шаблонов Group Policy. Без него каждый компьютер берет ADMX-файлы локально из своей Windows, из-за чего разные администраторы могут видеть разные политики или разные версии настроек. Central Store переносит все шаблоны в SYSVOL на контроллере домена, и после этого GPMC у всех начинает читать политики из одного общего места. Это делает управление GPO единообразным и позволяет централизованно добавлять новые шаблоны и тд и тп

#### PPS: при создании директории **contoso.com**\policies\PolicyDefinitions она не обязательно должна называться именно так, просто я балбес, можно назвать ее именем домена





