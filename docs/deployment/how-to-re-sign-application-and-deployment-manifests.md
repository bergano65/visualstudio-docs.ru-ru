---
title: 'Как: Повторное подписание Манифестов применения и развертывания Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc69ce1f79644d7f4b35fbb1c1e3a41691761390
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649190"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Практическое руководство. Повторное подписание манифестов приложения и развертывания
После внесения изменений в свойства развертывания в манифесте приложения для приложений Windows Forms, приложений Windows Presentation Foundation (xbap) или office-решений необходимо повторно подписать как приложения, так и манифесты развертывания с сертификатом. Этот процесс позволяет проверить, не установлены ли на компьютер конечного пользователя измененные злоумышленниками файлы.

 Другой сценарий, при котором вы можете повторно подписать манифесты, когда ваши клиенты хотят подписать приложение и развертывание манифестов с их собственным сертификатом.

## <a name="re-sign-the-application-and-deployment-manifests"></a>Повторное подписывание манифестов приложения и развертывания
 Эта процедура предполагает, что вы уже внесли изменения в файл манифеста приложения *(.manifest*). Для получения дополнительной информации [см.](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472)

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Повторное подписание приложения и развертывание с Mage.exe

1. Откройте окно **команды Visual Studio.**

2. Изменяйте каталоги в папку, содержащую файлы манифеста, которые вы хотите подписать.

3. Введите следующую команду, чтобы подписать файл манифеста приложения. Замените *ManifestFileName* с именем вашего файла манифеста плюс расширение. Замените *сертификат* относительной или полностью квалифицированной траекторией файла сертификата и *замените пароль* паролем для сертификата.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Например, можно запустить следующую команду для подписания манифеста приложения для надстройки, приложения Windows Form или браузерного приложения Windows Presentation Foundation. Временные сертификаты, созданные Visual Studio, не рекомендуются для развертывания в производственных средах.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. Введите следующую команду для обновления и подписания файла развертывания манифеста, заменив имена заполнителей, как на предыдущем этапе.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Например, можно запустить следующую команду для обновления и подписания манифеста развертывания для надстройки Excel, приложения Windows Forms или браузерного приложения Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Дополнительно скопируйте манифест мастер-развертывания*\\\<(опубликовать имя приложения>.application)* в каталог развертывания версии *(опубликовать приложение>_\\\<версии>).\< *

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Обновление и повторное подписание манифестов приложения и развертывания
 Эта процедура предполагает, что вы уже внесли изменения в файл манифеста приложения *(.manifest),* но есть и другие файлы, которые были обновлены. При обновлении файлов необходимо также обновить хэш, представляющий файл.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Обновление и повторное подписание манифестов приложения и развертывания с помощью Mage.exe

1. Откройте окно **команды Visual Studio.**

2. Изменяйте каталоги в папку, содержащую файлы манифеста, которые вы хотите подписать.

3. Удалите расширение файла *.deploy* из файлов в папке вывода публикации.

4. Введите следующую команду для обновления манифеста приложения с новыми хэшами для обновленных файлов и подпишите файл манифеста приложения. Замените *ManifestFileName* с именем вашего файла манифеста плюс расширение. Замените *сертификат* относительной или полностью квалифицированной траекторией файла сертификата и *замените пароль* паролем для сертификата.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Например, можно запустить следующую команду для подписания манифеста приложения для надстройки, приложения Windows Form или браузерного приложения Windows Presentation Foundation. Временные сертификаты, созданные Visual Studio, не рекомендуются для развертывания в производственных средах.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Введите следующую команду для обновления и подписания файла развертывания манифеста, заменив имена заполнителей, как на предыдущем этапе.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Например, можно запустить следующую команду для обновления и подписания манифеста развертывания для надстройки Excel, приложения Windows Forms или браузерного приложения Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. Добавьте расширение файла *.deploy* обратно в файлы, за исключением файлов манифеста приложения и развертывания.

7. Дополнительно скопируйте манифест мастер-развертывания*\\\<(опубликовать имя приложения>.application)* в каталог развертывания версии *(опубликовать приложение>_\\\<версии>).\< *

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
- [Практическое руководство. Настройка поведения запроса о доверии ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)