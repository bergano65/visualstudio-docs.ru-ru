---
title: Настройка поведения запроса о доверии ClickOnce | Документация Майкрософт
description: Узнайте, как настроить запрос о доверии ClickOnce для управления тем, предоставлены ли конечным пользователям возможность установки приложений ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8cb23eeee53990113d779e241adb8dcf1ab0cf16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890309"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Практическое руководство. Настройка поведения запроса о доверии ClickOnce
Вы можете настроить запрос о доверии ClickOnce, чтобы контролировать, предоставлены ли конечным пользователям возможность установки приложений ClickOnce, таких как Windows Forms приложения, Windows Presentation Foundation приложения, консольные приложения, приложения браузера WPF и решения Office. Запрос о доверии настраивается путем установки разделов реестра на каждом компьютере конечного пользователя.

 В следующей таблице показаны параметры конфигурации, которые можно применить к каждой из пяти зон (Internet, Унтрустедситес, MyComputer, LocalIntranet и Трустедситес).

|Параметр|Значение параметра реестра|Описание|
|------------|----------------------------|-----------------|
|Включите запрос о доверии.|`Enabled`|Запрос о доверии ClickOnce отображается таким образом, чтобы конечные пользователи могли предоставлять доверие приложениям ClickOnce.|
|Ограничьте запрос о доверии.|`AuthenticodeRequired`|Запрос о доверии ClickOnce отображается только в том случае, если приложения ClickOnce подписаны сертификатом, идентифицирующим издателя.|
|Отключить запрос о доверии.|`Disabled`|Запрос о доверии ClickOnce не отображается для приложений ClickOnce, которые не подписаны явно доверенным сертификатом.|

 В следующей таблице показано поведение по умолчанию для каждой зоны. В столбце приложения содержатся ссылки на Windows Forms приложения, Windows Presentation Foundation приложения, приложения браузера WPF и консольные приложения.

|Зона|Приложения|решения Office|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 Эти параметры можно переопределить, включив, запретив или отключив запрос о доверии ClickOnce.

## <a name="enable-the-clickonce-trust-prompt"></a>Включить запрос о доверии ClickOnce
 Включите запрос о доверии для зоны, если нужно, чтобы конечные пользователи преддавали возможность установки и запуска любого приложения ClickOnce, поступающих из этой зоны.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Включение запроса о доверии ClickOnce с помощью редактора реестра

1. Откройте редактор реестра:

    1. Нажмите кнопку **Пуск**, затем щелкните **Выполнить**.

    2. В поле **Открыть** введите `regedit` и нажмите кнопку **ОК**.

2. Найдите следующий раздел реестра:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Если раздел не существует, создайте его.

3. Добавьте следующие подразделы в качестве **строкового значения**, если они еще не существуют, со связанными значениями, приведенными в следующей таблице.

    |Подключ строкового значения|Значение|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Для решений Office `Internet` имеет значение по умолчанию `AuthenticodeRequired` и `UntrustedSites` имеет значение `Disabled` . Для всех остальных `Internet` параметров имеет значение по умолчанию `Enabled` .

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Включение запроса о доверии ClickOnce программными средствами

1. Создание Visual Basic или консольного приложения Visual C# в Visual Studio.

2. Откройте файл *Program. vb* или *Program.CS* для редактирования и добавьте следующий код.

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

3. Создайте и запустите приложение.

## <a name="restrict-the-clickonce-trust-prompt"></a>Ограничение запроса о доверии ClickOnce
 Ограничьте запрос о доверии, чтобы решения были подписаны сертификатами Authenticode с известными удостоверениями, прежде чем пользователи получат запрос на принятие решения о доверии.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Ограничение запроса о доверии ClickOnce с помощью редактора реестра

1. Откройте редактор реестра:

    1. Нажмите кнопку **Пуск**, затем щелкните **Выполнить**.

    2. В поле **Открыть** введите `regedit` и нажмите кнопку **ОК**.

2. Найдите следующий раздел реестра:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Если раздел не существует, создайте его.

3. Добавьте следующие подразделы в качестве **строкового значения**, если они еще не существуют, со связанными значениями, приведенными в следующей таблице.

    |Подключ строкового значения|Значение|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Ограничение запроса о доверии ClickOnce программным способом

1. Создание Visual Basic или консольного приложения Visual C# в Visual Studio.

2. Откройте файл *Program. vb* или *Program.CS* для редактирования и добавьте следующий код.

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

3. Создайте и запустите приложение.

## <a name="disable-the-clickonce-trust-prompt"></a>Отключить запрос о доверии ClickOnce
 Можно отключить запрос о доверии, чтобы конечные пользователи не могли устанавливать решения, которые еще не являются доверенными в политике безопасности.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Отключение запроса о доверии ClickOnce с помощью редактора реестра

1. Откройте редактор реестра:

    1. Нажмите кнопку **Пуск**, затем щелкните **Выполнить**.

    2. В поле **Открыть** введите `regedit` и нажмите кнопку **ОК**.

2. Найдите следующий раздел реестра:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Если раздел не существует, создайте его.

3. Добавьте следующие подразделы в качестве **строкового значения**, если они еще не существуют, со связанными значениями, приведенными в следующей таблице.

    |Подключ строкового значения|Значение|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Отключение запроса о доверии ClickOnce программным способом

1. Создание Visual Basic или консольного приложения Visual C# в Visual Studio.

2. Откройте файл *Program. vb* или *Program.CS* для редактирования и добавьте следующий код.

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

3. Выполните сборку и запустите приложение.

## <a name="see-also"></a>См. также раздел
- [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)
- [Управление доступом для кода для приложений ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce и технология Authenticode](../deployment/clickonce-and-authenticode.md)
- [Общие сведения о развертывании доверенных приложений](../deployment/trusted-application-deployment-overview.md)
- [Как включить параметры безопасности ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Как задать зону безопасности для приложения ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Как задать пользовательские разрешения для приложения ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Практическое руководство. Отладка приложения ClickOnce с ограниченными разрешениями](securing-clickonce-applications.md)
- [Практическое руководство. Добавление надежного издателя на клиентский компьютер для приложений ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Пошаговое руководство. Повторное подписание манифестов приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
