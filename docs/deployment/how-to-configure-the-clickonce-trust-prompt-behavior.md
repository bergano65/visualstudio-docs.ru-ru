---
title: 'Практическое: Настройка поведения запроса о доверии ClickOnce | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: badee4bfb98ef34f8d730f35d29f456d783d7d43
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155101"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Практическое: Настройка поведения запроса о доверии ClickOnce
Запрос о доверии ClickOnce для элемента управления можно настроить ли конечные пользователи получают возможность установки приложения ClickOnce, таких как приложения Windows Forms, приложения Windows Presentation Foundation, консольные приложения, браузере WPF приложения и решения Office. Настроить запрос о доверии путем задания разделов реестра на компьютере каждого конечного пользователя.  
  
 В следующей таблице показаны параметры конфигурации, которые могут применяться к каждому из пяти зон (Интернет, UntrustedSites, MyComputer, LocalIntranet и TrustedSites).  
  
|Параметр|Значение параметра реестра|Описание:|  
|------------|----------------------------|-----------------|  
|Разрешение запроса о доверии.|`Enabled`|Запрос о доверии ClickOnce отображается таким образом, чтобы конечным пользователям можно предоставить доверие для приложений ClickOnce.|  
|Ограничение запроса о доверии.|`AuthenticodeRequired`|Запрос о доверии ClickOnce отображается только в том случае, если приложение ClickOnce подписано сертификатом, который идентифицирует издателя.|  
|Отключите запрос о доверии.|`Disabled`|Запрос о доверии ClickOnce не отображается для любого приложения ClickOnce, не имеющие явно доверенным сертификатом.|  
  
 В следующей таблице показаны поведение по умолчанию для каждой зоны. Столбец приложений относится к приложений Windows Forms, приложения Windows Presentation Foundation, приложения браузера WPF и консольных приложений.  
  
|Зоны|Приложения|решения Office|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Эти параметры можно переопределить путем включения, ограничение или отключение запрос о доверии ClickOnce.  
  
## <a name="enable-the-clickonce-trust-prompt"></a>Включить запрос о доверии ClickOnce  
 Включите запрос о доверии для зоны, если нужно, чтобы конечные пользователи могут быть представлены с параметром установки и запуска приложения ClickOnce из этой зоны.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Чтобы включить запрос о доверии ClickOnce с помощью редактора реестра  
  
1.  Откройте редактор реестра:  
  
    1.  Нажмите кнопку **запустить**, а затем нажмите кнопку **запуска**.  
  
    2.  В **откройте** введите `regedit32`, а затем нажмите кнопку **ОК**.  
  
2.  Найдите следующий раздел реестра:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel**  
  
     Если ключ не существует, создайте его.  
  
3.  Добавьте следующие подразделы как **строковое значение**, если они еще не существует, с помощью связанных значений, приведенных в следующей таблице.  
  
    |Строковое значение подраздела|Значение|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Для решений Office `Internet` имеет значение по умолчанию `AuthenticodeRequired` и `UntrustedSites` имеет значение `Disabled`. Для всех остальных `Internet` имеет значение по умолчанию `Enabled`.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Программное Включение запрос о доверии ClickOnce  
  
1.  Создайте консольное приложение Visual Basic или Visual C# в Visual Studio.  
  
2.  Откройте *Program.vb* или *Program.cs* файл для редактирования и добавьте следующий код.  
  
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
  
## <a name="restrict-the-clickonce-trust-prompt"></a>Ограничить запрос о доверии ClickOnce  
 Ограничения запрос о доверии, таким образом, чтобы решения, которые должны быть подписаны с сертификатом Authenticode, идентифицирующим пользователям предлагается решение о доверии.  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Чтобы ограничить запрос о доверии ClickOnce с помощью редактора реестра  
  
1.  Откройте редактор реестра:  
  
    1.  Нажмите кнопку **запустить**, а затем нажмите кнопку **запуска**.  
  
    2.  В **откройте** введите `regedit`, а затем нажмите кнопку **ОК**.  
  
2.  Найдите следующий раздел реестра:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel** 
  
     Если ключ не существует, создайте его.  
  
3.  Добавьте следующие подразделы как **строковое значение**, если они еще не существует, с помощью связанных значений, приведенных в следующей таблице.  
  
    |Строковое значение подраздела|Значение|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Чтобы ограничить запрос о доверии ClickOnce программными средствами  
  
1.  Создайте консольное приложение Visual Basic или Visual C# в Visual Studio.  
  
2.  Откройте *Program.vb* или *Program.cs* файл для редактирования и добавьте следующий код.  
  
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
  
## <a name="disable-the-clickonce-trust-prompt"></a>Отключить запрос о доверии ClickOnce  
 Запрос о доверии можно отключить, чтобы конечные пользователи не получают возможность установить решения, которые уже не доверенным в политике безопасности.  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Чтобы отключить запрос о доверии ClickOnce с помощью редактора реестра  
  
1.  Откройте редактор реестра:  
  
    1.  Нажмите кнопку **запустить**, а затем нажмите кнопку **запуска**.  
  
    2.  В **откройте** введите `regedit`, а затем нажмите кнопку **ОК**.  
  
2.  Найдите следующий раздел реестра:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
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
  
2.  Откройте *Program.vb* или *Program.cs* файл для редактирования и добавьте следующий код.  
  
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
 [Разграничение доступа для приложений ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce и технология Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Общие сведения о развертывании доверенных приложений](../deployment/trusted-application-deployment-overview.md)   
 [Практическое: включить параметры безопасности ClickOnce-приложений](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Практическое: Установка зоны безопасности для ClickOnce-приложения](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Практическое: Установка пользовательских разрешений для ClickOnce-приложения](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Практическое: отладка ClickOnce-приложения с ограниченными разрешениями](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Практическое: Добавление надежного издателя на клиентский компьютер для приложений ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Практическое: повторное подписание манифестов приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md)