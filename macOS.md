1. [Как устроена архитектура macOS: что такое XNU, Darwin, Mach, BSD layer и I/O Kit, и как это влияет на модель безопасности системы?](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/e06fe546960c716c3b7b1fa380709956a9c1883f/soc/L1/base/mac1.md)
2. [Как в macOS устроены процессы, потоки и системные вызовы, и какие артефакты на уровне ОС могут быть полезны при расследовании вредоносной активности?](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/07301d76e80f2a8fa896cbbfa6e68edba4fedc1f/soc/L1/base/mac2.md)
3. [Основные элементы защиты macOS от впо](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/c1b68bba87b223c7ece8d95b14cb3e1d4f10153d/soc/L1/base/mac3.md)
4. [Что такое Mach-O как формат исполняемых файлов, чем .app отличается от обычного бинарника, и что смотреть при анализе подозрительного приложения?](https://github.com/tuzhilkina-em/StarterPack-of-InfoSec/blob/7867ff76a292f98df821ae2d9b8ae647176be9c8/soc/L1/base/mac4.md)
5. Что такое launchd, LaunchAgents и LaunchDaemons, как через них работает автозапуск и почему это один из главных механизмов persistence в macOS?
6. Где в macOS искать закрепление вредоноса: LaunchAgents, LaunchDaemons, Login Items, cron, shell profiles, browser extensions, configuration profiles
7. Как проверить подозрительный .plist: какие поля важны, какие пути подозрительны, как понять, что через него запускается вредоносный процесс?
8. Что такое code signing в macOS, зачем нужна подпись приложения, чем signed, unsigned, ad-hoc signed и modified signed binary отличаются с точки зрения риска?
9. Что такое notarization, Gatekeeper и quarantine attribute, как macOS решает, можно ли запускать скачанное из интернета приложение?
10. Как проверить происхождение и доверенность файла: подпись, notarization, quarantine attribute, extended attributes, путь запуска и источник загрузки?
11. Что такое SIP, почему root в macOS не всемогущий, какие области системы защищены и как это усложняет модификацию системных файлов вредоносом?
12. Что такое Signed System Volume, зачем macOS разделяет system volume и data volume, и как это влияет на защиту и форензику?
13. Что такое sandbox в macOS/iOS, какие ограничения он накладывает на приложения и зачем нужны entitlements?
14. Что такое TCC, какие доступы он контролирует, почему Full Disk Access, Accessibility и Screen Recording особенно опасны при компрометации?
15. Как вредонос может злоупотреблять Accessibility, Full Disk Access, Screen Recording или Apple Events, и какие признаки этого можно искать?
16. Что такое Keychain, какие данные в нем хранятся, как приложения получают к ним доступ и почему Keychain важен при расследовании компрометации учетных данных?
17. Что такое FileVault и APFS, что они защищают, а от чего не спасают, если пользователь уже вошел в систему?
18. Где в macOS смотреть логи безопасности: Unified Logging, log show, log stream, /var/log, install logs, auth-события, sudo, ssh, Gatekeeper, TCC?
19. Что такое Endpoint Security Framework, почему современные EDR на macOS используют его, и чем он лучше простого чтения логов?
20. Как провести первичный triage macOS-хоста: какие процессы, сетевые соединения, автозапуск, подписи, quarantine attributes, TCC-разрешения и логи проверить в первую очередь?
21. Какие типовые способы заражения macOS встречаются чаще всего: fake updates, cracked software, malicious .dmg, .pkg, .app, вредоносные расширения?
22. Какие встроенные утилиты macOS могут использоваться злоумышленником для living-off-the-land: curl, bash, osascript, python, sqlite3, launchctl, security?
23. Почему osascript и AppleScript могут быть опасны, какие действия они позволяют автоматизировать и как это может выглядеть в атаке?
24. Как обнаруживать сетевую активность вредоноса на macOS: активные соединения, listening ports, DNS-запросы, beaconing, C2, нестандартные направления трафика?
25. Какие встроенные защитные механизмы есть в macOS: Gatekeeper, XProtect, MRT, SIP, TCC, sandbox, FileVault, Application Firewall, Lockdown Mode, и какие у каждого ограничения?
26. Как проверить, что приложение потенциально опасно: подпись, notarization, entitlements, путь запуска, quarantine, сетевые соединения, автозапуск, доступы TCC?
27. Как расследовать подозрительный LaunchAgent или LaunchDaemon: где он лежит, что запускает, от какого пользователя, подписан ли бинарник, куда он подключается?
28. Как расследовать подозрительный сетевой процесс на macOS: найти PID, бинарник, подпись, родительский процесс, аргументы запуска, соединения и persistence?
29. Чем модель безопасности iOS жестче macOS: sandbox, entitlements, code signing, provisioning profiles, Secure Enclave, Data Protection, запрет произвольного выполнения кода?
30. Что такое Secure Enclave и Data Protection classes в iOS, какие данные они защищают и почему это важно для безопасности мобильных устройств?
31. Что такое jailbreak с точки зрения модели безопасности iOS, какие защитные механизмы он ослабляет и почему после jailbreak устройство становится более рискованным?
32. Как объяснить отличие macOS security от Windows security: code signing/notarization/TCC/SIP против Windows Defender, Event Log, UAC, ACL, AppLocker/WDAC, Sysmon?
33. Как объяснить отличие macOS security от Linux security: launchd против systemd, TCC/SIP/Gatekeeper против SELinux/AppArmor/auditd, .app/Mach-O против ELF/package-based модели?
34. Какие команды нужно знать для базового анализа macOS-хоста: ps, top, lsof, netstat, ifconfig, log show, log stream, launchctl, codesign, spctl, xattr, csrutil, fdesetup?
35. Какие признаки могут указывать на вредонос в macOS: запуск из /tmp или ~/Library, странный LaunchAgent, unsigned binary, подозрительные entitlements, обращение к C2, скрытые директории, использование curl | bash?
36. Какие действия пользователя чаще всего приводят к заражению macOS и какие защитные меры это снижают: запрет cracked software, контроль установки приложений, обновления, MDM, EDR, least privilege?
