## Что хранится в SYSVOL

На моей админской виртуалке это выглядит следующим образом: 

![njevsf](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/f039fd6ad6031c595a4a1c7b3255b272f29349e1/soc/L1/base/images/photo_2026-05-14%2016.23.20.jpeg)

[Документация по SYSVOL](https://learn.microsoft.com/ru-ru/troubleshoot/windows-server/group-policy/rebuild-sysvol-tree-and-content-in-a-domain)  


Вообще из разных источников информация разная, примерная сводка:

`Policies` - хранит GPO, внутри находятся папки с GUID каждой политики, содержащие `registry.pol`, scripts, preferences и administrative settings

`Scripts` - хранит logon/logoff/startup/shutdown scripts, используемые Group Policy

`NETLOGON` - общая SMB-шара для хранения logon scripts и файлов, доступных доменным клиентам при аутентификации

`GPT.ini` - файл версии GPO, используется клиентами и DC для определения изменений политики

`registry.pol` - бинарное хранилище registry-based настроек GPO для Computer и User Configuration

`Machine` - часть GPO с computer settings, startup scripts и computer registry policies

`User` - часть GPO с user settings, logon scripts и user registry policies

`Preferences` - хранит Group Policy Preferences, например drive mapping, scheduled tasks и local users

`Adm/ADMX references` - административные шаблоны и ссылки на policy definitions, используемые GPMC

`DFSR metadata` - служебные данные DFS Replication для репликации SYSVOL между DC

`Security templates` - параметры security policy, включая rights assignment и audit policy

`Applications and Services data` - данные некоторых расширений Group Policy и CSE (Client Side Extensions)
