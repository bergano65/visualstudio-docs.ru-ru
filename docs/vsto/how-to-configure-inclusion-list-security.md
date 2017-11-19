---
title: "Как: настройка безопасности списка включения | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
ms.assetid: 0609d8f0-4630-4e17-aeb3-14f3134165cf
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7032f3663be7df1a06fa4dc16d4f4473e4666cfc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-configure-inclusion-list-security"></a>Практическое руководство. Настройка безопасности списка включения
  При наличии разрешений администратора, можно настроить [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] запросы о доверии к элементу управления, получают ли конечным пользователям возможности установки решений Office, сохранив решение о доверии в списке включения. Сведения о списках включений см. в разделе [предоставление доверия решениям Office с помощью списков включения](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Для решений, в каждой из пяти зон можно задать следующие параметры:  
  
-   Включить [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] раздела запроса о доверии и списка включения. Можно разрешить конечным пользователям предоставлять доверие решениям Office, подписанные с любой сертификат.  
  
-   Ограничить [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] раздела запроса о доверии и списка включения. Можно разрешить конечным пользователям для установки решений Office, подписанным сертификатом, который идентифицирует издателя, но который еще не является доверенным.  
  
-   Отключить [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] раздела запроса о доверии и списка включения. Можно запретить пользователям установке решения Office, не подписана с явно доверенным сертификатом.  
  
## <a name="enabling-the-inclusion-list"></a>Включение списка включения  
 Включите список включения для зоны, если нужно, чтобы конечным пользователям будет предложена возможность установки и запуска решения Office, поступающих из этой зоны.  
  
#### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Чтобы включить в список включения с помощью редактора реестра  
  
1.  Откройте редактор реестра:  
  
    1.  Нажмите кнопку **запустить**, а затем нажмите кнопку **запуска**.  
  
    2.  В **откройте** введите **regedt32.exe**, а затем нажмите кнопку **ОК**.  
  
2.  Найдите следующий раздел реестра:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Если ключ не существует, создайте его.  
  
3.  Добавьте следующие подразделы как **строковое значение**, если они еще не существуют, со связанными значениями.  
  
    |Строковое значение подраздела|Значение|  
    |-------------------------|-----------|  
    |**Интернет**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**Отключено**|  
    |**Мой компьютер**|**Включено**|  
    |**Локальная интрасеть**|**Включено**|  
    |**TrustedSites**|**Включено**|  
  
     По умолчанию **Internet** имеет значение **AuthenticodeRequired** и **UntrustedSites** имеет значение **отключено**.  
  
#### <a name="to-enable-the-inclusion-list-programmatically"></a>Программное Включение списка включения  
  
1.  Создайте консольное приложение Visual Basic или Visual C#.  
  
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
  
3.  Выполните сборку и запуск приложения.  
  
## <a name="restricting-the-inclusion-list"></a>Ограничение списка включения  
 Ограничение списка включения, чтобы решения должны быть подписаны сертификатом Authenticode, идентифицирующим пользователям предлагается решение о доверии.  
  
#### <a name="to-restrict-the-inclusion-list"></a>Ограничение списка включения  
  
1.  Откройте редактор реестра:  
  
    1.  Нажмите кнопку **запустить**, а затем нажмите кнопку **запуска**.  
  
    2.  В **откройте** введите **regedt32.exe**, а затем нажмите кнопку **ОК**.  
  
2.  Найдите следующий раздел реестра:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Если ключ не существует, создайте его.  
  
3.  Добавьте следующие подразделы как **строковое значение**, если они еще не существуют, со связанными значениями.  
  
    |Строковое значение подраздела|Значение|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**Отключено**|  
    |**Интернет**|**AuthenticodeRequired**|  
    |**Мой компьютер**|**AuthenticodeRequired**|  
    |**Локальная интрасеть**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     По умолчанию **Internet** имеет значение **AuthenticodeRequired** и **UntrustedSites** имеет значение **отключено**.  
  
#### <a name="to-restrict-the-inclusion-list-programmatically"></a>Ограничение списка включения программными средствами  
  
1.  Создайте консольное приложение Visual Basic или Visual C#.  
  
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
  
3.  Выполните сборку и запуск приложения.  
  
## <a name="disabling-the-inclusion-list"></a>Отключение списка включения  
 Можно отключить список включения, чтобы конечные пользователи могут только устанавливать решений, подписанным с надежный и известный сертификат.  
  
#### <a name="to-disable-the-inclusion-list"></a>Отключение списка включения  
  
1.  Откройте редактор реестра:  
  
    1.  Нажмите кнопку **запустить**, а затем нажмите кнопку **запуска**.  
  
    2.  В **откройте** введите **regedt32.exe**, а затем нажмите кнопку **ОК**.  
  
2.  Если это еще не существует, создайте следующий раздел реестра:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
3.  Добавьте следующие подразделы как **строковое значение**, если они еще не существуют, со связанными значениями.  
  
    |Строковое значение подраздела|Значение|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**Отключено**|  
    |**Интернет**|**Отключено**|  
    |**Мой компьютер**|**Отключено**|  
    |**Локальная интрасеть**|**Отключено**|  
    |**TrustedSites**|**Отключено**|  
  
#### <a name="to-disable-the-inclusion-list-programmatically"></a>Чтобы отключить списка включения программными средствами  
  
1.  Создайте консольное приложение Visual Basic или Visual C#.  
  
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
  
3.  Выполните сборку и запуск приложения.  
  
## <a name="see-also"></a>См. также  
 [Предоставление доверия решениям Office с помощью списков включения](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)  
  
  