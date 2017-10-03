---
title: "Задание свойств соединения | Документы Microsoft"
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1b62700-f046-488d-bd6b-a5cd8fc345b7
caps.latest.revision: 154
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 56dbb81f9d30ccb41a6247c4fefda9d6ecd703a6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setting-the-connection-properties"></a>Задание свойств соединения
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Свойства строки подключения могут быть заданы различными способами.  
  
-   Как имя = значение свойства в URL-АДРЕСЕ соединения при подключении с помощью класса DriverManager.  
  
-   Как имя = значение свойства в *свойства* параметра метода Connect класса DriverManager.  
  
-   С помощью аргумента соответствующего метода задания свойств источника данных драйвера. Например:  
  
    ```  
  
    datasource.setServerName(value)  
    datasource.setDatabaseName(value)  
  
    ```  
  
## <a name="remarks"></a>Замечания  
 В именах свойств не учитывается регистр символов. Дублирующиеся имена свойств разрешаются в следующем порядке:  
  
1.  аргументы API (например, имя пользователя и пароль);  
  
2.  Коллекция свойств.  
  
3.  Последний экземпляр в строке подключения.  
  
 Кроме того, разрешено использование свойств с неизвестными драйверу именами. Их значения не проверяются драйвером JDBC на предмет учета регистра символов.  
  
 Допускается использование синонимов, которые разрешаются в порядке очередности, аналогично повторяющимся именам свойств.  
  
 В следующей таблице перечислены все доступные на данный момент свойства строки подключения для драйвера JDBC.  
  
|Свойство|Тип|По умолчанию|Description|  
|--------------|----------|-------------|-----------------|  
|accessToken|Строковые значения|null|Это свойство можно используйте для подключения к базе данных SQL с помощью маркера доступа. **accessToken** невозможно задать, используя URL-адрес подключения.|  
|applicationIntent|Строковые значения|ReadWrite|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможными значениями являются **ReadOnly** и **ReadWrite**. Дополнительные сведения см. в разделе [драйвер JDBC поддерживает высокий уровень доступности и аварийного восстановления](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md).|  
|applicationName|Строковые значения<br /><br /> [<=128 символов]|null|Имя приложения или «[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]», если имя не указано. Используется для идентификации определенных приложений в различных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] профилирования и средства ведения журнала.|  
|проверка подлинности|Строковые значения|Не указан|Начиная с Microsoft JDBC Driver 6.0 для SQL Server, это дополнительное свойство указывает, какой метод проверки подлинности SQL для подключения. Возможными значениями являются **ActiveDirectoryIntegrated**, **ActiveDirectoryPassword**, **SqlPassword** и значение по умолчанию **NotSpecified**.<br /><br /> Используйте **ActiveDirectoryIntegrated** для подключения к базе данных SQL, используя встроенную проверку подлинности Windows.<br /><br /> Используйте **ActiveDirectoryPassword** для подключения к базе данных SQL с помощью Azure AD основное имя и пароль.<br /><br /> Используйте **SqlPassword** для подключения к SQL Server с помощью **userName**/**пользователя** и **пароль** свойства.<br /><br /> Используйте **NotSpecified** Если ни один из этих методов проверки подлинности необходима.<br /><br /> **Важно:** проверки подлинности значение ActiveDirectoryIntegrated, следующие две библиотеки будет необходимо установить: **SQLJDBC_AUTH. Библиотеки DLL** (доступно в пакете драйверов JDBC) и Azure Active Directory Authentication Library для SQL Server (**ADALSQL. Библиотеки DLL**) она доступна на нескольких языках (x86 и amd64) из центра загрузки [Microsoft библиотеку аутентификации Active Directory для Microsoft SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=48742). Драйвер JDBC поддерживает только версию **1.0.2028.318 и более поздних версиях** для ADALSQL. БИБЛИОТЕКИ DLL.<br /><br /> **Примечание:** при проверки подлинности задано любое значение, отличное от **NotSpecified**, по умолчанию драйвер использует шифрование Secure Sockets Layer (SSL).<br /><br /> Сведения о настройке проверки подлинности Azure Active Directory [подключение к SQL базы данных с использованием Azure Active Directory проверки подлинности](https://azure.microsoft.com/en-us/documentation/articles/sql-database-aad-authentication/).|  
|authenticationScheme|Строковые значения|«NativeAuthentication»|Указывает, какой тип встроенной безопасности должен использоваться приложением. Возможными значениями являются **JavaKerberos** и значение по умолчанию **NativeAuthentication**.<br /><br /> При использовании **authenticationScheme = JavaKerberos**, необходимо указать полное доменное имя (FQDN) в **serverName** или **serverSpn** свойство. В противном случае возникнет ошибка «Сервер не найден в базе данных Kerberos».<br /><br /> Дополнительные сведения об использовании **authenticationScheme**, в разделе [с помощью встроенной проверки подлинности Kerberos для подключения к SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).|  
|columnEncryptionSetting|Строковые значения<br /><br /> [«Enabled» &#124;» Отключено]»|Выключено|Значение «Enabled» для использования в начало функции Always Encrypted (AE) с Microsoft JDBC Driver 6.0 для SQL Server. Когда функция Always Encrypted включена, драйвер JDBC прозрачно шифрует и расшифровывает конфиденциальные данные, хранящиеся в столбцах зашифрованной базы данных в SQL Server.<br /><br /> В разделе [использование постоянного шифрования с драйвером JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md) для получения дополнительных сведений.<br /><br /> **Примечание:** постоянное шифрование доступно с SQL Server 2016 или более поздней версии.|  
|databaseName, database|Строковые значения<br /><br /> [<=128 символов]|null|Имя базы данных для соединения. Если не установлено, подключение выполняется к базе данных по умолчанию.|  
|disableStatementPooling|boolean<br /><br /> [«true» &#124;» значение false»]|true|В настоящее время поддерживается только значение true. Если задано значение false, возникает исключение.|  
|encrypt|boolean<br /><br /> [«true» &#124;» значение false»]|false|Задайте значение «true», чтобы указать, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] использует шифрование Secure Sockets Layer (SSL) для всех данных, передаваемых между клиентом и сервером, если сервер имеет установленный сертификат. Значение по умолчанию — false.<br /><br /> Начиная с Microsoft JDBC Driver 6.0 для SQL Server, имеется новый параметр подключения «authentication», с использованием шифрования SSL по умолчанию. Дополнительные сведения см. свойство «проверки подлинности».|  
|failoverPartner|Строковые значения|null|Имя сервера отработки отказа, используемого в конфигурации зеркального отображения базы данных. Это свойство используется при ошибке первоначального подключения к основному серверу. После выполнения первоначального подключения это свойство игнорируется. Должно использоваться совместно со свойством databaseName.<br /><br /> **Примечание:** драйвер не поддерживает указание номер порта экземпляра сервера для экземпляра-участника отработки отказа в составе свойства failoverPartner в строке подключения. Однако поддерживается указание свойств serverName, instanceName и portNumber экземпляра основного сервера и свойства failoverPartner экземпляра партнера по обеспечению отработки отказа в одной строке подключения.<br /><br /> Если указать имя виртуальной сети в **сервера** свойство соединения нельзя использовать зеркальное отображение базы данных. В разделе [драйвер JDBC поддерживает высокий уровень доступности и аварийного восстановления](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) для получения дополнительной информации.|  
|hostNameInCertificate|Строковые значения|null|Имя узла для использования при проверке [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL-сертификат.<br /><br /> Если свойство hostNameInCertificate не задано или задано значение null, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] будет использовать **serverName** значения свойства в URL-АДРЕСЕ соединения имени узла для проверки [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL-сертификат.<br /><br /> **Примечание:** это свойство используется в сочетании с **шифрования**/**проверки подлинности** свойства и **trustServerCertificate**свойство. Это свойство влияет на проверку сертификата только в том случае, если соединение использует шифрование Secure Sockets Layer (SSL) и **trustServerCertificate** имеет значение «false». Убедитесь, что значение, передаваемое **hostNameInCertificate** точно соответствует общее имя (CN) или DNS-имя в альтернативное имя СУБЪЕКТА в сертификате сервера для SSL-соединения для успешного выполнения. Дополнительные сведения см. в разделе [основные сведения о поддержке SSL](../../connect/jdbc/understanding-ssl-support.md).|  
|INSTANCENAME|Строковые значения<br /><br /> [<=128 символов]|null|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Имя экземпляра для подключения. Если не задано, подключение выполняется к экземпляру по умолчанию. В случае, когда указан порт и instanceName, см. примечания к порту.<br /><br /> Если указать имя виртуальной сети в **сервера** свойство соединения нельзя использовать **instanceName** свойство соединения. В разделе [драйвер JDBC поддерживает высокий уровень доступности и аварийного восстановления](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) для получения дополнительной информации.|  
|integratedSecurity|boolean<br /><br /> [«true» &#124;» значение false»]|false|Установите значение «true», чтобы указать, что учетные данные Windows будет использоваться [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в операционных системах Windows. Если установлено значение true, драйвер JDBC выполняет поиск учетных данных, которые уже были предоставлены при входе в сеть или на компьютер, в локальном кэше учетных данных компьютера.<br /><br /> Имеет значение «true» (с **authenticationscheme = JavaKerberos**), чтобы указать, что учетные данные Kerberos будет использоваться [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Дополнительные сведения о проверке подлинности Kerberos см. в разделе [с помощью встроенной проверки подлинности Kerberos для подключения к SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md). <br /><br /> Если установлено значение false, необходимо будет предоставить имя пользователя и пароль.| 
|keyStoreAuthentication|Строковые значения|null| Начиная с Microsoft JDBC Driver 6.0 для SQL Server, это свойство определяет, какие хранилища ключей, чтобы легко настроить для соединения с постоянным шифрованием и определяет механизм проверки подлинности, используемый для проверки подлинности в хранилище ключей. Microsoft JDBC Driver 6.0 для SQL Server поддерживает параметр размером хранилища ключей Java без проблем с помощью этого свойства, для которого необходимо задать «**keyStoreAuthentication = JavaKeyStorePassword**». Обратите внимание, что для использования этого свойства, необходимо также задать **keyStoreLocation** и **keyStoreSecret** свойств для хранилища ключей Java. <br/><br/>Дополнительные сведения см. на сайте [использование постоянного шифрования с драйвером JDBC](https://msdn.microsoft.com/library/mt591987%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396). 
|keyStoreLocation|Строковые значения|null|Когда **keyStoreAuthentication = JavaKeyStorePassword**, **keyStoreLocation** свойство определяет путь к файл хранилище ключей Java с помощью главного ключа столбца для использования с постоянным шифрованием данные. Обратите внимание, что путь должен включать имя файла хранилища ключей.<br/><br/>Дополнительные сведения см. на сайте [использование постоянного шифрования с драйвером JDBC](https://msdn.microsoft.com/library/mt591987%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396).
|keyStoreSecret|Строковые значения|null|Когда **keyStoreAuthentication = JavaKeyStorePassword**, **keyStoreSecret** свойство определяет пароль, используемый для хранилище ключей, а также как и для ключа. Обратите внимание, что для использования в хранилище ключей Java хранилище ключей и пароль ключа должны быть одинаковыми.<br/><br/>Дополнительные сведения см. на сайте [использование постоянного шифрования с драйвером JDBC](https://msdn.microsoft.com/library/mt591987%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396).
|lastUpdateCount|boolean<br /><br /> [«true» &#124;» значение false»]|true|Если установлено значение true, возвращается только последнее значение счетчика обновлений из инструкции SQL, переданной серверу. Оно может быть использовано в одной из инструкций SELECT, INSERT, DELETE, чтобы игнорировать последующие изменения счетчика обновлений, вызываемые триггерами сервера. Установка для этого свойства значения false влечет за собой возврат всех значений счетчика обновлений, включая изменения, вызванные триггерами сервера.<br /><br /> **Примечание:** это свойство применяется только при использовании с [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) методы. Все остальные выполнение методы возвращают все результаты и значения счетчика обновлений. Это свойство влияет только на значения счетчика обновлений, возвращаемые триггерами сервера. Оно не влияет на результирующие наборы или ошибки, возникшие в процессе выполнения триггеров.|  
|lockTimeout|int|-1|Время в миллисекундах, по истечении которого база данных сообщает об истечении времени ожидания блокировки. Режим по умолчанию — время ожидания неограничено. Если задано, это значение по умолчанию для всех инструкций в подключении. Обратите внимание, что **Statement.setQueryTimeout()** может использоваться для установки времени ожидания для определенных инструкций. Значение может быть равным 0 — время ожидания отсутствует.|  
|loginTimeout|int [0..65535]|15|Время в секундах, по истечении которого драйвер инициирует превышение времени ожидания неудачного подключения. Нулевое значение указывает, что время ожидания равно системному времени ожидания по умолчанию, которое по умолчанию составляет 15 секунд. Ненулевое значение представляет время в секундах, по истечении которого драйвер инициирует превышение времени ожидания неудачного подключения.<br /><br /> Если указать имя виртуальной сети в **сервера** свойство подключения, необходимо задать значение времени ожидания три минуты или более, чтобы предоставить достаточно времени для успешного соединения отработки отказа. В разделе [драйвер JDBC поддерживает высокий уровень доступности и аварийного восстановления](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) для получения дополнительной информации.|  
|multiSubnetFailover|Логическое значение|false|Всегда указывайте **multiSubnetFailover = true** при подключении к прослушивателю группы доступности из [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] группы доступности или [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] экземпляра отказоустойчивого кластера. **multiSubnetFailover = true** настраивает [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] для обеспечения более быстрое обнаружение и подключение к серверу (активного). Допустимые значения — true и false. В разделе [драйвер JDBC поддерживает высокий уровень доступности и аварийного восстановления](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) для получения дополнительной информации.<br /><br /> Можно программно обращаться к **multiSubnetFailover** свойство соединения с [getPropertyInfo](../../connect/jdbc/reference/getpropertyinfo-method-sqlserverdriver.md), [getMultiSubnetFailover](../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md), и [ setMultiSubnetFailover](../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md).<br /><br /> **Примечание:** начиная с Microsoft JDBC Driver 6.0 для SQL Server больше не требуется задать multiSubnetFailover в значение true при подключении к прослушивателю группы доступности. Новое свойство **transparentNetworkIPResolution**, который включен по умолчанию обеспечивает обнаружение и подключение к серверу (активного).|  
|packetSize|int [-1 &#124; 0 &#124; 512..32767]|8000|Размер (в байтах) сетевого пакета, используемого для обмена данными с SQL Server. Значение -1 указывает на использование размера сетевого пакета сервера по умолчанию. Значение 0 указывает на использование максимального значения — 32767. Если этому свойству задано значение за пределами допустимого диапазона значений, возникнет исключение.<br /><br /> **Важно:** не рекомендуется использовать свойство packetSize при включенном шифровании (зашифровать = true). В противном случае в работе драйвера может быть вызвана ошибка подключения. Дополнительные сведения см. в разделе [setPacketSize](../../connect/jdbc/reference/setpacketsize-method-sqlserverdatasource.md) метод [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) класса.|  
|password|Строковые значения<br /><br /> [<=128 символов]|null|Пароль базы данных в случае подключения с SQL пользователя и пароль.<BR/>Для соединений Kerberos с основным именем и паролем это свойство имеет значение пароль участника Kerberos.|  
|portNumber, порт|int [0..65535]|1433|Порт где [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ожидает передачи данных. Если номер порта задан в строке подключения, запросы к sqlbrowser не выполняются. В случае, когда указан порт и instanceName, подключение выполняется к указанному порту. Тем не менее **instanceName** проверяется и если оно не соответствует порту, возникает ошибка.<br /><br /> **Важно:** рекомендуется номер порта всегда указать, как это более безопасно, чем использование sqlbrowser.|  
|responseBuffering|Строковые значения<br /><br /> [«full» &#124;» Adaptive]»|adaptive|Если свойство имеет значение adaptive, это указывает на буферизацию необходимого минимума данных. По умолчанию используется режим adaptive.<br /><br /> Если свойство имеет значение full, при выполнении инструкции выполняется чтение с сервера результирующего набора полностью.<br /><br /> **Примечание:** после обновления драйвера JDBC с версии 1.2, поведение буферизации по умолчанию будет «adaptive». Если ваше приложение никогда не задает свойство «responseBuffering», и вы хотите сохранить поведение версии 1.2 по умолчанию в приложении, необходимо задать свойству responseBufferring значение «полная» в свойствах соединения или с помощью [ setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) метод [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|selectMethod|Строковые значения<br /><br /> [«direct» &#124;» курсор»]|direct|Если этому свойству задано значение cursor, то для каждого созданного в этом соединении запроса создается курсор базы данных с параметрами TYPE_FORWARD_ONLY, CONCUR_READ_ONLY. Это свойство обычно необходимо, только если приложение создает очень большие результирующие наборы, которые не могут полностью находится в клиентской памяти. Если свойство имеет значение cursor, в клиентской памяти сохраняется ограниченное число строк результирующего набора. Режим по умолчанию — все строки результирующего набора сохраняются в клиентской памяти. Такой вариант обеспечивает наибольшую производительность, когда приложение обрабатывает все строки.|  
|sendStringParametersAsUnicode|boolean<br /><br /> [«true» &#124;» значение false»]|true|Если **sendStringParametersAsUnicode** задано значение «true», строковые параметры отправляются на сервер в Юникоде.<br /><br /> Если **sendStringParametersAsUnicode** имеет значение «false», строковые параметры отправляются на сервер в формате Юникод, например ASCII/MBCS, а не в Юникоде.<br /><br /> Значение по умолчанию для **sendStringParametersAsUnicode** свойство имеет значение «true».<br /><br /> **Примечание:** **sendStringParametersAsUnicode** свойство проверяется только при отправке значения параметра, имеющего **CHAR**, **VARCHAR**, или **LONGVARCHAR** типов JDBC. Новые методы национальных кодировок JDBC 4.0, например методы setNString, setNCharacterStream и setNClob [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) классы всегда значения своих параметров отправки на сервер в Юникоде независимо от значения этого свойства.<br /><br /> Для достижения оптимальной производительности **CHAR**, **VARCHAR**, и **LONGVARCHAR** типов данных JDBC, приложение должно установить ** sendStringParametersAsUnicode** значение «false» и использование setString, setCharacterStream и методы, не поддерживающие национальные символы setClob [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [ SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) классы.<br /><br /> Когда приложение задает **sendStringParametersAsUnicode** значение «false» и использует метод без национальных символов для доступа к данным в Юникоде типов на стороне сервера (таких как **nchar**, **nvarchar** и **ntext**), некоторые данные могут быть потеряны, если параметры сортировки базы данных не поддерживает символы в строковых параметрах, которые передаются методом, не поддерживающие национальные символы.<br /><br /> Обратите внимание, что приложение должно использовать методы национальных символов setNString, setNCharacterStream и setNClob из [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) классы для **NCHAR**, **NVARCHAR**, и **LONGNVARCHAR** типов данных JDBC.|  
|sendTimeAsDatetime|boolean<br /><br /> [«true» &#124;» значение false»]|true|Это свойство было добавлено в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC.<br /><br /> Если значение равно true, значения java.sql.Time будут отправляться на сервер в качестве [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **datetime** значения.<br /><br /> Если значение равно false, значения java.sql.Time будут отправляться на сервер в качестве [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **время** значения.<br /><br /> **sendTimeAsDatetime** можно также можно изменять программным образом с [SQLServerDataSource.setSendTimeAsDatetime](../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).<br /><br /> Значение по умолчанию этого свойства в будущей версии может быть изменено.<br /><br /> Дополнительные сведения о том, как [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] настраивает значения java.sql.Time перед их отправкой на сервер, в разделе [Настройка как значения java.sql.Time отправляются на сервер](../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).|  
|serverName, server|Строковые значения|null|Компьютер под управлением [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br /> Можно также указать имя виртуальной сети [!INCLUDE[ssHADR](../../includes/sshadr_md.md)] группы доступности. В разделе [драйвер JDBC поддерживает высокий уровень доступности и аварийного восстановления](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) для получения дополнительной информации.|  
|serverSpn|Строковые значения|null|Начиная с версии Microsoft JDBC Driver 4.2 для SQL Server это необязательное свойство можно использовать для указания имени субъекта-службы (SPN) соединения Java Kerberos.  Он используется в сочетании с **authenticationScheme**.<br /><br /> Чтобы указать имя участника-службы, он может быть в форме: «MSSQLSvc/fqdn:port@REALM» где fqdn — это полное доменное имя, port — Номер порта и REALM — это область Kerberos SQL Server в верхнем регистре.<br /><br /> Примечание: @REALM является обязательным, если область по умолчанию клиента (как указано в конфигурации Kerberos) совпадает с областью Kerberos для SQL Server.<br /><br /> Дополнительные сведения об использовании **serverSpn** с Java Kerberos в разделе [с помощью встроенной проверки подлинности Kerberos для подключения к SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).|  
|serverNameAsACE|boolean<br /><br /> [«true» &#124;» значение false»]|false|Начиная с Microsoft JDBC Driver 6.0 для SQL Server, задайте значение true, чтобы указать, что драйвер должен преобразовать имя сервера в формате Юникода в ASCII-совместимую кодировку (Punycode) для данного подключения. Если этот параметр имеет значение false, драйвер подключается с использованием имени сервера, указанного пользователем.<br /><br /> В разделе [международные функции драйвера JDBC](../../connect/jdbc/international-features-of-the-jdbc-driver.md) для получения дополнительных сведений.|  
|TransparentNetworkIPResolution|boolean<br /><br /> [«true» &#124;» значение false»]|true|Начиная с Microsoft JDBC Driver 6.0 для SQL Server, это свойство, transparentNetworkIPResolution, обеспечивает более быстрое обнаружение и подключение к серверу (активного). Возможные значения: true и false с true как значение по умолчанию.<br /><br /> До появления Microsoft JDBC Driver 6.0 для SQL Server, приложение было задайте строку подключения, чтобы включить «multiSubnetFailover = true» для указания, что он был при подключении к группе доступности AlwaysOn. Без указания ключевого слова подключения multiSubnetFailover в значение true, приложение может столкнуться с истечения времени ожидания при подключении к группе доступности. Начиная с Microsoft JDBC Driver 6.0 для SQL Server, приложение не нужно задавать multiSubnetFailover в значение true, больше. <br /><br />**Примечание:** при transparentNetworkIPResolution = true, первая попытка соединения использует 500 мс как время ожидания. Все последующие попытками использовать одну и ту же логику времени ожидания, что свойство multiSubnetFailover.|  
|columnEncryptionSetting|boolean<br /><br /> [«true» &#124;» значение false»]|false|Задайте значение true для использования функции Always Encrypted (AE), начиная с Microsoft JDBC Driver 6.0 для SQL Server. Когда функция Always Encrypted включена, драйвер JDBC прозрачно шифрует и расшифровывает конфиденциальные данные, хранящиеся в столбцах зашифрованной базы данных в SQL Server.<br /><br /> В разделе [использование постоянного шифрования с драйвером JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md) для получения дополнительных сведений.<br /><br /> **Примечание:** постоянное шифрование доступно с SQL Server 2016 или более новых версий.|  
|trustServerCertificate|boolean<br /><br /> [«true» &#124;» значение false»]|false|Задайте значение «true», чтобы указать, что [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] не будет проверять [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL-сертификат.<br /><br /> Если «true», [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL-сертификат автоматически считается доверенным, когда на уровне связи применяется шифрование SSL.<br /><br /> Если «false», [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] будет проверять SSL-сертификата сервера. Если проверка сертификата сервера завершается ошибкой, в работе драйвера будет вызвана ошибка, и соединение будет разорвано. Значение по умолчанию — «false». Убедитесь, что значение, передаваемое **serverName** точно соответствует общее имя (CN) или DNS-имя в альтернативное имя субъекта в сертификате сервера для SSL-соединения для успешного выполнения. Дополнительные сведения см. в разделе [основные сведения о поддержке SSL](../../connect/jdbc/understanding-ssl-support.md).<br /><br /> **Примечание:** это свойство используется в сочетании с **шифрования**/**проверки подлинности** свойства. Это свойство влияет только на проверку SSL-сертификата сервера только в том случае, если соединение использует шифрование SSL.|  
|trustStore|Строковые значения|null|Путь к файлу сертификата trustStore (включая имя файла). Файл trustStore содержит список сертификатов, которым доверяет клиент.<br /><br /> Когда свойство не задано или имеет значение null, драйвер будет использовать правила поиска фабрики диспетчеров доверия, чтобы определить, какой из хранящихся сертификатов необходимо использовать.<br /><br /> **Значение по умолчанию фабрика SunX509 TrustManagerFactory пытается найти доверенный в следующем порядке:**<br /><br /> Файл, указанный системным свойством javax.net.ssl.trustStore виртуальной машины Java (JVM).<br /><br /> «\<java-home >/lib/безопасность/jssecacerts» файла.<br /><br /> «\<java-home >/lib/безопасность/cacerts» файла.<br /><br /> <br /><br /> Дополнительные сведения см. в документации по интерфейсу SUNX509 TrustManager на веб-сайте компании Sun Microsystems.<br /><br /> **Примечание:** это свойство влияет только на поиск сертификата trustStore только в том случае, если соединение использует шифрование SSL и **trustServerCertificate** задано значение «false».|  
|trustStorePassword|Строковые значения|null|Пароль, используемый для проверки целостности данных trustStore.<br /><br /> Если задано свойство trustStore, а свойство trustStorePassword не задано, проверка целостности trustStore не выполняется.<br /><br /> Если значение не задано как для свойства trustStore, так и для свойства trustStorePassword, драйвер будет использовать системные свойства виртуальной машины Java javax.net.ssl.trustStore и javax.net.ssl.trustStorePassword. Если не задано значение системного свойства "javax.net.ssl.trustStorePassword", проверка целостности trustStore не выполняется.<br /><br /> Если свойство trustStore не задано, а свойство trustStorePassword задано, драйвер JDBC будет использовать файл, заданный "javax.net.ssl.trustStore" в качестве доверенного хранилища, целостность доверенного хранилища проверяется с использованием указанного trustStorePassword. Это может потребоваться в случае, если клиентское приложение не желает сохранять пароль с системном свойстве JVM.<br /><br /> **Примечание:** свойство trustStorePassword влияет только на поиск сертификата trustStore только в том случае, если соединение использует SSL-соединение и **trustServerCertificate** задано значение «false».|  
|userName, user|Строковые значения<br /><br /> [<=128 символов]|null|Пользователь базы данных в случае подключения с SQL пользователя и пароль.<BR/>Для соединений Kerberos с основным именем и паролем этому свойству присвоено имя участника Kerberos.|  
|workstationID|Строковые значения<br /><br /> [<=128 символов]|\<пустая строка >|Идентификатор рабочей станции. Используется для идентификации определенной рабочей станции в различных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] профилирования и средства ведения журнала. Если не указано, \<пустая строка > используется.|  
|xopenStates|boolean<br /><br /> [«true» &#124;» значение false»]|false|Установите значение true, чтобы указать, что драйвер возвращает в исключениях коды состояний, совместимые с XOPEN. Значение по умолчанию — возвращать коды состояний SQL 99.|  
|gsscredential|org.ietf.jgss.GSSCredential|null|Начиная с 6.2 драйвер JDBC Microsoft SQL Server, учетные данные пользователя, используемый для ограниченного делегирования Kerberos могут передаваться в этом свойстве. <BR/>Этот параметр следует использовать с **integratedSecurity** как **true** и **JavaKerberos** **authenticationscheme**.| 
|jaasConfigurationName|Строковые значения|SQLJDBCDriver|Начиная с 6.2 драйвер JDBC Microsoft SQL Server, каждого подключения к SQL Server может иметь свой собственный файл конфигурации входа JAAS подключение Kerberos. Имя файла конфигурации входа могут передаваться через это свойство. <BR/> По умолчанию драйвер устанавливает свойство `useDefaultCcache = true` для JVM IBM и `useTicketCache = true` для других JVM.|
|serverPreparedStatementDiscardThreshold|Целочисленный|10|Определяет, сколько действия отклонения необработанных подготовленной инструкции (sp_unprepare) может быть обработки для соединения, перед выполнением вызов очистки незавершенные обработчики на сервере. Если значение параметра — < = 1 un-Подготовка действия выполняются немедленно для подготовленной инструкции close. Если задано значение > 1, эти вызовы будут объединены, чтобы избежать вызова sp_unprepare слишком часто.|
|enablePrepareOnFirstPreparedStatementCall|boolean<br /><br /> [«true» &#124;» значение false»]|false|Если эта конфигурация имеет значение false первого выполнения подготовленной инструкции вызовите процедуры sp_executesql и не Подготовка инструкции, после второго выполнения происходит его вызывает sp_prepexec и фактически установки дескриптор подготовленной инструкции.|
|statementPoolingCacheSize|Целочисленный|10|Можно настроить кэшируемые инструкции для повторного использования в пуле| 
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Принимает используемые на сервере значения по умолчанию для свойства соединения, за исключением ANSI_DEFAULTS и IMPLICIT_TRANSACTIONS. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Автоматически устанавливает свойство ANSI_DEFAULTS в значение ON и IMPLICIT_TRANSACTIONS значение OFF.  

> [!Note]
> Важно: Если проверка подлинности задано значение ActiveDirectoryPassword, следующая библиотека потребуется должны быть включены в пути к классам: [azure-activedirectory библиотека for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java). Его можно найти на [Maven репозитория](https://mvnrepository.com/artifact/com.microsoft.azure/adal4j). Самый простой способ загрузки библиотеки и ее зависимостей является использование Maven. 
 >1. Во-первых установите Maven в системе 
 >2. Последовательно выберите пункты [странице GitHub](https://github.com/Microsoft/mssql-jdbc) драйвера
 >3. Загрузите файл pom.xml
 >4. Выполните следующую команду для загрузки библиотеки и его зависимости Maven: mvn зависимостей: copy-зависимости
  
## <a name="see-also"></a>См. также:  
 [Подключение к SQL Server с помощью драйвера JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
 [Режим FIPS](../../connect/jdbc/fips-mode.md)
  
  
