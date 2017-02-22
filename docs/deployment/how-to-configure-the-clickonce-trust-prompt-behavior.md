---
title: "Практическое руководство. Настройка поведения запроса о доверии ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "приложения ClickOnce, установка без запроса"
  - "приложения ClickOnce, запросы о доверии"
  - "развертывание ClickOnce, установка без запроса"
  - "развертывание ClickOnce, запросы о доверии"
  - "развертывание приложений [ClickOnce], запросы о доверии"
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Практическое руководство. Настройка поведения запроса о доверии ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Запрос о доверии ClickOnce можно настроить таким образом, чтобы оставить за пользователем решение об установке таких приложений ClickOnce, как приложения Windows Forms и Windows Presentation Foundation, консольные приложения, приложения браузера WPF и решения для Office.  Настройка запроса о доверии осуществляется путем настройки разделов реестра на всех пользовательских компьютерах.  
  
 В следующей таблице приведены параметры конфигурации для каждой из пяти зон \(Internet, UntrustedSites, MyComputer, LocalIntranet и TrustedSites\).  
  
|Параметр|Значение параметра реестра|Описание|  
|--------------|--------------------------------|--------------|  
|Разрешить запрос о доверии|`Enabled`|Запрос о доверии ClickOnce позволяет пользователю решить, доверяет ли он приложению ClickOnce.|  
|Ограничить запрос о доверии|`AuthenticodeRequired`|Запрос о доверии ClickOnce выводится только в том случае, если приложение ClickOnce подписано сертификатом, который идентифицирует издателя.|  
|Запретить запрос о доверии|`Disabled`|Запрос о доверии ClickOnce не будет выведен, если приложение ClickOnce не подписано явно доверенным сертификатом.|  
  
 В следующей таблице приведено поведение по умолчанию для каждой зоны.  Значения в столбце "Приложения" относятся к консольным приложениям, приложениям Windows Forms, Windows Presentation Foundation и приложениям браузера WPF.  
  
|Зона|Приложения|Решения для Office|  
|----------|----------------|------------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`Локальная интрасеть (LocalIntranet)`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Эти параметры можно переопределить, разрешая, запрещая или ограничивая запрос о доверии ClickOnce.  
  
## Разрешение запроса о доверии ClickOnce  
 Запрос о доверии для той или иной зоны следует разрешать в случае, если выбор о допустимости установки и запуска приложения ClickOnce из этой зоны решено предоставить пользователю.  
  
#### Разрешение запроса о доверии ClickOnce при помощи редактора реестра  
  
1.  Откройте редактор реестра. Для этого выполните следующее:  
  
    1.  В меню **Пуск** выберите команду **Выполнить**.  
  
    2.  В поле **Открыть** введите `regedit32` и нажмите кнопку **ОК**.  
  
2.  Найдите следующий раздел реестра:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Если раздел не существует, создайте его.  
  
3.  Если соответствующих **строковых параметров** не существует, создайте их, а затем установите для них значения, указанные в следующей таблице.  
  
    |Строковое значение подраздела|Значение|  
    |-----------------------------------|--------------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`Локальная интрасеть (LocalIntranet)`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Для решений для Office параметр `Internet` имеет по умолчанию значение `AuthenticodeRequired`, а параметр `UntrustedSites` — значение `Disabled`.  Во всех прочих случаях параметр `Internet` по умолчанию имеет значение `Enabled`.  
  
#### Разрешение запроса о доверии ClickOnce программными средствами  
  
1.  Создайте в Visual Studio консольное приложение Visual Basic или Visual C\#.  
  
2.  Откройте для редактирования файл Program.vb или Program.cs и добавьте следующий код.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Постройте и запустите приложение.  
  
## Ограничение запроса о доверии ClickOnce  
 Вывод запроса о доверии может выполняться \(и, соответственно, выбор может возлагаться на пользователя\) только в том случае, если решение подписано сертификатом Authenticode, идентифицирующим разработчика.  
  
#### Ограничение запроса о доверии ClickOnce при помощи редактора реестра  
  
1.  Откройте редактор реестра. Для этого выполните следующее:  
  
    1.  В меню **Пуск** выберите команду **Выполнить**.  
  
    2.  В поле **Открыть** введите `regedit` и нажмите кнопку **ОК**.  
  
2.  Найдите следующий раздел реестра:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Если раздел не существует, создайте его.  
  
3.  Если соответствующих **строковых параметров** не существует, создайте их, а затем установите для них значения, указанные в следующей таблице.  
  
    |Строковое значение подраздела|Значение|  
    |-----------------------------------|--------------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`Локальная интрасеть (LocalIntranet)`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### Ограничение запроса о доверии ClickOnce программными средствами  
  
1.  Создайте в Visual Studio консольное приложение Visual Basic или Visual C\#.  
  
2.  Откройте для редактирования файл Program.vb или Program.cs и добавьте следующий код.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Постройте и запустите приложение.  
  
## Запрещение запроса о доверии ClickOnce  
 Можно запретить вывод запроса о доверии и тем самым лишить конечных пользователей возможности устанавливать решения, которые не были ранее признаны доверенными согласно политике безопасности.  
  
#### Запрещение запроса о доверии ClickOnce при помощи редактора реестра  
  
1.  Откройте редактор реестра. Для этого выполните следующее:  
  
    1.  В меню **Пуск** выберите команду **Выполнить**.  
  
    2.  В поле **Открыть** введите `regedit` и нажмите кнопку **ОК**.  
  
2.  Найдите следующий раздел реестра:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Если раздел не существует, создайте его.  
  
3.  Если соответствующих **строковых параметров** не существует, создайте их, а затем установите для них значения, указанные в следующей таблице.  
  
    |Строковое значение подраздела|Значение|  
    |-----------------------------------|--------------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`Локальная интрасеть (LocalIntranet)`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### Запрещение запроса о доверии ClickOnce программными средствами  
  
1.  Создайте в Visual Studio консольное приложение Visual Basic или Visual C\#.  
  
2.  Откройте для редактирования файл Program.vb или Program.cs и добавьте следующий код.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3.  Постройте и запустите приложение.  
  
## См. также  
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Управление доступом для кода для приложения ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce и технология Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Общие сведения о развертывании доверенных приложений](../deployment/trusted-application-deployment-overview.md)   
 [Практическое руководство. Включение параметров безопасности ClickOnce\-приложений.](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Практическое руководство. Установка зоны безопасности для ClickOnce\-приложения](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Практическое руководство. Установка пользовательских разрешений для ClickOnce\-приложения](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Практическое руководство. Отладка ClickOnce\-приложения с ограниченными разрешениями](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Инструкции: добавление надежного издателя на клиентский компьютер для приложений ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Практическое руководство. Повторное подписание манифестов приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md)