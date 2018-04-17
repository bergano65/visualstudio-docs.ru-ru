---
title: 'Как: Настройка поведения запроса о доверии ClickOnce | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: e3a399a9f075249f2457c431385132476b173191
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Практическое руководство. Настройка поведения запроса о доверии ClickOnce
Можно настроить запрос о доверии ClickOnce для элемента управления пользователи получают возможность установки приложения ClickOnce, таких как приложения Windows Forms, приложениях Windows Presentation Foundation, консольные приложения, браузера WPF приложений и решений Office. Настроить запрос о доверии при установке разделов реестра на компьютере для каждого конечного пользователя.  
  
 В следующей таблице показаны параметры конфигурации, которые могут применяться к каждой из пяти зон (Интернета, UntrustedSites, MyComputer, локальная интрасеть и TrustedSites).  
  
|Параметр|Значение параметра реестра|Описание|  
|------------|----------------------------|-----------------|  
|Разрешение запроса о доверии.|`Enabled`|Запрос о доверии ClickOnce отображается, чтобы конечным пользователям можно предоставить доверие приложения ClickOnce.|  
|Ограничение запроса о доверии.|`AuthenticodeRequired`|Запрос о доверии ClickOnce отображается только в том случае, если приложение ClickOnce подписано сертификатом, который идентифицирует издателя.|  
|Отключите запрос о доверии.|`Disabled`|Запрос о доверии ClickOnce не отображается для любого приложения ClickOnce, не имеющие явно доверенным сертификатом.|  
  
 В следующей таблице показано поведение по умолчанию для каждой зоны. Столбец приложений относится приложения Windows Forms, приложениях Windows Presentation Foundation, приложения браузера WPF и консольных приложений.  
  
|Зоны|Приложения|решения Office|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Эти параметры можно переопределить, включая, ограничивая или отключение запроса о доверии ClickOnce.  
  
## <a name="enabling-the-clickonce-trust-prompt"></a>Включение запрос о доверии ClickOnce  
 Разрешение запроса о доверии для зоны, если нужно конечным пользователям будет предложена возможность установки и запуска приложения ClickOnce из этой зоны.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Чтобы включить запрос о доверии ClickOnce при помощи редактора реестра  
  
1.  Откройте редактор реестра:  
  
    1.  Нажмите кнопку **запустить**, а затем нажмите кнопку **запуска**.  
  
    2.  В **откройте** введите `regedit32`, а затем нажмите кнопку **ОК**.  
  
2.  Найдите следующий раздел реестра:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Если ключ не существует, создайте его.  
  
3.  Добавьте следующие подразделы как **строковое значение**, если они еще не существует, с помощью связанных значений, приведенных в следующей таблице.  
  
    |Строковое значение подраздела|Значение|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Для решений Office `Internet` имеет значение по умолчанию `AuthenticodeRequired` и `UntrustedSites` имеет значение `Disabled`. Во всех прочих случаях `Internet` имеет значение по умолчанию `Enabled`.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Чтобы включить запрос о доверии ClickOnce программными средствами  
  
1.  Создайте консольное приложение Visual Basic или Visual C# в Visual Studio.  
  
2.  Откройте для редактирования файл Program.vb или Program.cs и добавьте следующий код.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
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
  
## <a name="restricting-the-clickonce-trust-prompt"></a>Ограничение запроса о доверии ClickOnce  
 Ограничение запроса о доверии, чтобы решения должны быть подписаны сертификатом Authenticode, идентифицирующим пользователям предлагается решение о доверии.  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Чтобы ограничить запрос о доверии ClickOnce с помощью редактора реестра  
  
1.  Откройте редактор реестра:  
  
    1.  Нажмите кнопку **запустить**, а затем нажмите кнопку **запуска**.  
  
    2.  В **откройте** введите `regedit`, а затем нажмите кнопку **ОК**.  
  
2.  Найдите следующий раздел реестра:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Если ключ не существует, создайте его.  
  
3.  Добавьте следующие подразделы как **строковое значение**, если они еще не существует, с помощью связанных значений, приведенных в следующей таблице.  
  
    |Строковое значение подраздела|Значение|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Ограничение запроса о доверии ClickOnce программными средствами  
  
1.  Создайте консольное приложение Visual Basic или Visual C# в Visual Studio.  
  
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
  
## <a name="disabling-the-clickonce-trust-prompt"></a>Отключение запрос о доверии ClickOnce  
 Запрос о доверии можно отключить, чтобы конечные пользователи не получают возможность установки решения, которые уже не доверенным в политике безопасности.  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Чтобы отключить запрос о доверии ClickOnce при помощи редактора реестра  
  
1.  Откройте редактор реестра:  
  
    1.  Нажмите кнопку **запустить**, а затем нажмите кнопку **запуска**.  
  
    2.  В **откройте** введите `regedit`, а затем нажмите кнопку **ОК**.  
  
2.  Найдите следующий раздел реестра:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Если ключ не существует, создайте его.  
  
3.  Добавьте следующие подразделы как **строковое значение**, если они еще не существует, с помощью связанных значений, приведенных в следующей таблице.  
  
    |Строковое значение подраздела|Значение|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Чтобы отключить запрос о доверии ClickOnce программными средствами  
  
1.  Создайте консольное приложение Visual Basic или Visual C# в Visual Studio.  
  
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
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Управление доступом для кода для приложения ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce и технология Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Общие сведения о развертывании доверенных приложений](../deployment/trusted-application-deployment-overview.md)   
 [Практическое руководство. Включение параметров безопасности ClickOnce-приложений.](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Практическое руководство. Установка зоны безопасности для ClickOnce-приложения](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Практическое руководство. Установка пользовательских разрешений для ClickOnce-приложения](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Практическое руководство. Отладка ClickOnce-приложения с ограниченными разрешениями](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Как: Добавление надежного издателя на клиентский компьютер для приложений ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Практическое руководство. Повторное подписание манифестов приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md)