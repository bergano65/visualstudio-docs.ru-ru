---
title: "Практическое руководство. Настройка безопасности списка включения | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "списки включения [разработка решений Office в Visual Studio]"
  - "разрешения [разработка решений Office в Visual Studio"
ms.assetid: 0609d8f0-4630-4e17-aeb3-14f3134165cf
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Практическое руководство. Настройка безопасности списка включения
  При наличии прав администратора можно настроить запрос о доверии [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)], чтобы управлять предоставлением пользователям возможности установки решений Office, сохранив решение о доверии в списке включения.  Дополнительные сведения о списках включения см. в разделе [Предоставление доверия решениям Office с помощью списков включения](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Для решений, находящихся в каждой из пяти зон, можно установить следующие параметры:  
  
-   Включение раздела запроса о доверии [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] и списка включения.  Можно разрешить конечным пользователям предоставлять доверие решениям Office, подписанным каким\-либо сертификатом.  
  
-   Ограничение раздела запроса о доверии [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] и списка включения.  Можно разрешить конечным пользователям устанавливать решения Office, подписанные сертификатом, который идентифицирует издателя, но который еще не является доверенным.  
  
-   Отключение раздела запроса о доверии [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] и списка включения.  Можно предотвратить установку конечными пользователями решения Office, не подписанного явно доверенным сертификатом.  
  
## Включение списка включения  
 Включите список включения для зоны, если нужно предоставить пользователям возможность установки и запуска любых решений Office, поступающих из этой зоны.  
  
#### Включение списка включения при помощи редактора реестра  
  
1.  Откройте редактор реестра. Для этого выполните следующее:  
  
    1.  В меню **Пуск** выберите команду **Выполнить**.  
  
    2.  В окне **Открыть** введите **regedt32.exe** и нажмите кнопку **ОК**.  
  
2.  Найдите следующий раздел реестра:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Если раздел не существует, создайте его.  
  
3.  Добавьте следующие подразделы как **строковое значение**, если они еще не существуют, со связанными значениями.  
  
    |Строковое значение подраздела|Значение|  
    |-----------------------------------|--------------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**Disabled**|  
    |**MyComputer**|**Enabled**|  
    |**Локальная интрасеть \(LocalIntranet\)**|**Enabled**|  
    |**TrustedSites**|**Enabled**|  
  
     По умолчанию **Internet** имеет значение **AuthenticodeRequired**, а **UntrustedSites** имеет значение **Disabled**.  
  
#### Включение списка включения программными средствами  
  
1.  Создайте консольное приложение Visual Basic или Visual C\#.  
  
2.  Откройте для редактирования файл Program.vb или Program.cs и добавьте следующий код.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## Ограничение списка включения  
 Задайте ограничение для списка включения так, чтобы решения должны быть подписаны сертификатами Authenticode, имеющими известное удостоверение, до того как от пользователей будет запрошено решение о доверии.  
  
#### Ограничение списка включения  
  
1.  Откройте редактор реестра. Для этого выполните следующее:  
  
    1.  В меню **Пуск** выберите команду **Выполнить**.  
  
    2.  В окне **Открыть** введите **regedt32.exe** и нажмите кнопку **ОК**.  
  
2.  Найдите следующий раздел реестра:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Если раздел не существует, создайте его.  
  
3.  Добавьте следующие подразделы как **строковое значение**, если они еще не существуют, со связанными значениями.  
  
    |Строковое значение подраздела|Значение|  
    |-----------------------------------|--------------|  
    |**UntrustedSites**|**Disabled**|  
    |**Internet**|**AuthenticodeRequired**|  
    |**MyComputer**|**AuthenticodeRequired**|  
    |**Локальная интрасеть \(LocalIntranet\)**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     По умолчанию **Internet** имеет значение **AuthenticodeRequired**, а **UntrustedSites** имеет значение **Disabled**.  
  
#### Ограничение списка включения программными средствами  
  
1.  Создайте консольное приложение Visual Basic или Visual C\#.  
  
2.  Откройте для редактирования файл Program.vb или Program.cs и добавьте следующий код.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## Отключение списка включения  
 Можно отключить список включения, так чтобы конечные пользователи могли устанавливать решения, подписанным доверенным и известным сертификатом.  
  
#### Отключение списка включения  
  
1.  Откройте редактор реестра. Для этого выполните следующее:  
  
    1.  В меню **Пуск** выберите команду **Выполнить**.  
  
    2.  В окне **Открыть** введите **regedt32.exe** и нажмите кнопку **ОК**.  
  
2.  Создайте следующий раздел реестра, если он еще не существует.  
  
     **\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel**  
  
3.  Добавьте следующие подразделы как **строковое значение**, если они еще не существуют, со связанными значениями.  
  
    |Строковое значение подраздела|Значение|  
    |-----------------------------------|--------------|  
    |**UntrustedSites**|**Disabled**|  
    |**Internet**|**Disabled**|  
    |**MyComputer**|**Disabled**|  
    |**Локальная интрасеть \(LocalIntranet\)**|**Disabled**|  
    |**TrustedSites**|**Disabled**|  
  
#### Отключение списка включения программными средствами  
  
1.  Создайте консольное приложение Visual Basic или Visual C\#.  
  
2.  Откройте для редактирования файл Program.vb или Program.cs и добавьте следующий код.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
 [Предоставление доверия решениям Office с помощью списков включения](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)  
  
  