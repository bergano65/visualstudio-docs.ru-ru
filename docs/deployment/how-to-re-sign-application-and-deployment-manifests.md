---
title: 'Как: повторной подписи манифестов приложения и развертывания | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba634ffb30d6459c940811f0ea080f8b71a37f34
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31566138"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Практическое руководство. Повторное подписание манифестов приложения и развертывания
После внесения изменений в свойства развертывания в манифесте приложения для приложений Windows Forms, приложениях Windows Presentation Foundation (xbap) или решений Office, необходимо заново подписать приложение и манифесты развертывания с сертификат. Этот процесс гарантирует, что измененные злоумышленниками файлы не установлены на компьютерах конечных пользователей.  
  
 Другой сценарий, где могут заново подписывать манифесты при клиентам необходимо подписать приложение и манифесты развертывания своим собственным сертификатом.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Повторное подписывание приложения и развертывания манифестов  
 Эта процедура предполагает, что вы уже внесены изменения в файл манифеста приложения (с расширением MANIFEST). Дополнительные сведения см. в разделе [как: изменить свойства развертывания](http://msdn.microsoft.com/en-us/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Для повторной подписи приложения и развертывания манифестов с помощью Mage.exe  
  
1.  Откройте **командной строки Visual Studio** окна.  
  
2.  Перейдите в папку, содержащую файлы манифеста, которые вы хотите войти.  
  
3.  Введите следующую команду, чтобы подписать файл манифеста приложения. Замените на имя файла манифеста, а также расширение ManifestFileName. Заменить сертификат относительный или полный путь к файлу сертификата и замените пароль пароль для сертификата.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Например можно выполнить следующую команду для подписания манифеста приложения для надстройки, приложение Windows Forms или приложение браузера Windows Presentation Foundation. Временные сертификаты, созданные с помощью Visual Studio для развертывания в рабочей среде не рекомендуется.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Введите следующую команду, чтобы обновить и подписать файл манифеста развертывания, заменив местозаполнители, как в предыдущем действии.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Например можно выполнить следующую команду, чтобы обновить и подписать манифест развертывания для надстройки Excel, в приложении Windows Forms или приложение браузера Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  При необходимости скопируйте основной манифест развертывания (публикация\\*appname*.application) в каталог развертывания версии (файлы publish\Application\\*appname*_ *версии*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Обновление и повторное подписание манифестов приложения и развертывания  
 Эта процедура предполагает, что вы уже внесены изменения в приложение (с расширением MANIFEST) файл манифеста, однако, существуют другие файлы, которые были обновлены. При обновлении файлов, необходимо также обновить хэш, который представляет файл.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Обновление и повторное подписание приложения и развертывания манифестов с Mage.exe  
  
1.  Откройте **командной строки Visual Studio** окна.  
  
2.  Перейдите в папку, содержащую файлы манифеста, которые вы хотите войти.  
  
3.  Удалите расширение .deploy из файлов в папке выходных данных публикации.  
  
4.  Введите следующую команду, чтобы обновить манифест приложения с новыми хэшами для обновленных файлов и подписать файл манифеста приложения. Замените на имя файла манифеста, а также расширение ManifestFileName. Заменить сертификат относительный или полный путь к файлу сертификата и замените пароль пароль для сертификата.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Например можно выполнить следующую команду для подписания манифеста приложения для надстройки, приложение Windows Forms или приложение браузера Windows Presentation Foundation. Временные сертификаты, созданные с помощью Visual Studio для развертывания в рабочей среде не рекомендуется.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Введите следующую команду, чтобы обновить и подписать файл манифеста развертывания, заменив местозаполнители, как в предыдущем действии.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Например можно выполнить следующую команду, чтобы обновить и подписать манифест развертывания для надстройки Excel, в приложении Windows Forms или приложение браузера Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Добавьте расширение .deploy файлы, за исключением файлов манифеста приложения и развертывания.  
  
7.  При необходимости скопируйте основной манифест развертывания (публикация\\*appname*.application) в каталог развертывания версии (файлы publish\Application\\*appname*_ *версии*).  
  
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
 [Практическое руководство. Настройка поведения запроса о доверии ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)