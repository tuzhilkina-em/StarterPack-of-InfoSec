## Fine-Grained Password Policy
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ***Fine-Grained Password Policy, FGPP*** - механизм Active Directory, позволяющий назначать разные парольные политики разным пользователям или группам внутри одного домена. До появления FGPP в Active Directory существовала только одна доменная парольная политика, которая адавалась через Default Domain Policy и применялась ко всем учетным записям домена одновременно, что гарантировало одинаковые критерии безопасности для всех пользователей  


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Начиная с Windows Server 2008 появился механизм Fine-Grained Password Policies, он требует функциональный уровень домена не ниже Windows Server 2008. FGPP внутри Active Directory как специальные объекты - **Password Settings Object (PSO)**, которые, в свою очередь хранятся в контейнере CN=Password Settings Container,CN=System,DC=domain,DC=local. Внутри PSO содержатся параметры:
- минимальная длина пароля
- password history
- maximum password age
- minimum password age
- password complexity
- reversible encryption
- lockout threshold
- lockout duration
- observation window  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Когда пользователь пытается изменить пароль или пройти аутентификацию, контроллер домена определяет, какая парольная политика должна применяться именно к этой учетной записи. Обработка идет не через OU и не через inheritance GPO. FGPP применяется только напрямую к пользователю или через глобальные security groups. Если пользователь попадает под несколько PSO одновременно, используется атрибут msDS-PasswordSettingsPrecedence. Чем меньше значение precedence, тем выше приоритет    


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Если PSO отсутствует, применяется обычная доменная парольная политика из Default Domain Policy. То есть FGPP не заменяет доменную парольную политику полностью, скорее работает как override-механизм поверх стандартной domain password policy, при чем применяется он только к пользакам и группам безопасности. При аутентификации LSASS запрашивает у AD effective password settings пользователя. Для этого используется атрибут msDS-ResultantPSO. Он показывает, какая именно политика в итоге применяется к пользователю, еще это провряется с помощью Get-ADUserResultantPasswordPolicу  
