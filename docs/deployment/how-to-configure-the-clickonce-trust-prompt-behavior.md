---
title: 'Как: Настройка ClickOnce Доверие Оперативное поведение (ru) Документы Майкрософт'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec5f1cca49f1b799b39969849e0a73bf1e6e296d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649151"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Практическое руководство. Настройка поведения запроса о доверии ClickOnce
Вы можете настроить подсказку доверия ClickOnce, чтобы контролировать, предоставляется ли конечным пользователям возможность установки приложений ClickOnce, таких как приложения Форм Windows, приложения Windows Presentation Foundation, консольные приложения, приложения для браузеров WPF и решения Office. Вы настраиваете запрос доверия, установив ключи реестра на компьютере каждого пользователя.

 В следующей таблице показаны параметры конфигурации, которые могут быть применены к каждой из пяти зон (Интернет, UntrustedSites, MyComputer, LocalIntranet и TrustedSites).

|Параметр|Значение настройки реестра|Описание|
|------------|----------------------------|-----------------|
|Включите подсказку доверия.|`Enabled`|ClickOnce целевой запрос отображается так, что конечные пользователи могут предоставить доверие ClickOnce приложений.|
|Ограничьте запрос доверия.|`AuthenticodeRequired`|Подсказка доверия ClickOnce отображается только в том случае, если приложения ClickOnce подписаны сертификатом, идентифицируя издателя.|
|Отвачьте подсказку доверия.|`Disabled`|Подсказка ClickOnce доверия не отображается для любых приложений ClickOnce, которые не подписаны явно доверенным сертификатом.|

 В следующей таблице показано поведение по умолчанию для каждой зоны. В колонке приложений приложений Приложений Windows Forms, приложений Фонда презентации Windows, браузерных приложений WPF и консольных приложений.

|Зона|Приложения|решения Office|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 Эти параметры можно переопределить, включив, ограничив или отключив подсказку доверия ClickOnce.

## <a name="enable-the-clickonce-trust-prompt"></a>Включить подсказку доверия ClickOnce
 Включите запрос доверия для зоны, когда вы хотите, чтобы конечным пользователям была представлена возможность установки и запуска любого приложения ClickOnce, которое поступает из этой зоны.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Для того, чтобы подсказка доверия ClickOnce с помощью редактора реестра

1. Откройте редактор реестра:

    1. Нажмите кнопку **Пуск** и выберите команду **Выполнить**.

    2. В **открытой** коробке, введите, `regedit`а затем нажмите **OK**.

2. Найти следующий ключ реестра:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Если ключ не существует, создайте его.

3. Добавьте следующие подключи в качестве **значения строки,** если они еще не существуют, с соответствующими значениями, указанными в следующей таблице.

    |Подключка значения строки|Значение|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Для решений `Internet` Office, имеет `AuthenticodeRequired` `UntrustedSites` значение по `Disabled`умолчанию и имеет значение. Для всех `Internet` остальных значение `Enabled`по умолчанию.

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Для того, чтобы доверие ClickOnce подскажут программно

1. Создайте приложение Visual Basic или Visual C' в Visual Studio.

2. Откройте *файл Program.vb* или *Program.cs* для редактирования и добавьте следующий код.

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

3. Выполните сборку и запустите приложение.

## <a name="restrict-the-clickonce-trust-prompt"></a>Ограничьте подсказку доверия ClickOnce
 Ограничьте подсказку доверия, чтобы решения должны быть подписаны сертификатами Authenticode, которые знали личность до того, как пользователям будет предложено принять решение о доверии.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Чтобы ограничить подсказку доверия ClickOnce с помощью редактора реестра

1. Откройте редактор реестра:

    1. Нажмите кнопку **Пуск** и выберите команду **Выполнить**.

    2. В **открытой** коробке, введите, `regedit`а затем нажмите **OK**.

2. Найти следующий ключ реестра:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Если ключ не существует, создайте его.

3. Добавьте следующие подключи в качестве **значения строки,** если они еще не существуют, с соответствующими значениями, указанными в следующей таблице.

    |Подключка значения строки|Значение|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Чтобы ограничить доверие ClickOnce быстро программно

1. Создайте приложение Visual Basic или Visual C' в Visual Studio.

2. Откройте *файл Program.vb* или *Program.cs* для редактирования и добавьте следующий код.

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

3. Выполните сборку и запустите приложение.

## <a name="disable-the-clickonce-trust-prompt"></a>Отключить подсказку доверия ClickOnce
 Можно отключить запрос доверия, чтобы конечным пользователям не была предоставлена возможность установки решений, которым уже не доверяют в их политике безопасности.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Чтобы отключить подсказку доверия ClickOnce с помощью редактора реестра

1. Откройте редактор реестра:

    1. Нажмите кнопку **Пуск** и выберите команду **Выполнить**.

    2. В **открытой** коробке, введите, `regedit`а затем нажмите **OK**.

2. Найти следующий ключ реестра:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Если ключ не существует, создайте его.

3. Добавьте следующие подключи в качестве **значения строки,** если они еще не существуют, с соответствующими значениями, указанными в следующей таблице.

    |Подключка значения строки|Значение|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Чтобы отключить ClickOnce доверия оперативно программно

1. Создайте приложение Visual Basic или Visual C' в Visual Studio.

2. Откройте *файл Program.vb* или *Program.cs* для редактирования и добавьте следующий код.

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

## <a name="see-also"></a>См. также
- [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)
- [Управление доступом для кода для приложений ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce и технология Authenticode](../deployment/clickonce-and-authenticode.md)
- [Общие сведения о развертывании доверенных приложений](../deployment/trusted-application-deployment-overview.md)
- [Как: Включить настройки безопасности ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Практическое руководство. Установка зоны безопасности для ClickOnce-приложения](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Практическое руководство. Установка пользовательских разрешений для приложения ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Практическое руководство. Отладка приложения ClickOnce с ограниченными разрешениями](securing-clickonce-applications.md)
- [Практическое руководство. Добавление надежного издателя на клиентский компьютер для приложений ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Как: Повторное подписание приложений и развертывания манифестов](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
