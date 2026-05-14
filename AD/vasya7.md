## Что хранится в SYSVOL

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
