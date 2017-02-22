---
title: "Практическое руководство. Повторное подписание манифестов приложения и развертывания | Microsoft Docs"
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
  - "развертывание ClickOnce, подписание манифеста"
  - "развертывание приложений [ClickOnce], подписание манифеста"
  - "развертывание приложений, подписание манифеста"
  - "приложения Office, подписание манифеста"
  - "Office - разработка решений в Visual Studio, подписание манифеста"
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Практическое руководство. Повторное подписание манифестов приложения и развертывания
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

После внесения изменений в свойства развертывания в манифесте приложений Windows Forms, приложений Windows Presentation Foundation \(xbap\) или решений Office необходимо выполнить повторное подписание манифестов приложения и развертывания с помощью сертификата.  Это позволяет не допустить установки поддельных файлов на компьютерах конечных пользователей.  
  
 Кроме того, повторное подписание манифестов может потребоваться в том случае, если пользователи подписывают манифесты приложения и развертывания своими сертификатами.  
  
## Повторное подписание манифестов приложения и развертывания  
 Эта процедура предполагает, что в файл манифеста приложения \(MANIFEST\) уже внесены изменения.  Дополнительные сведения см. в разделе [Практическое руководство. Изменение свойств развертывания](http://msdn.microsoft.com/ru-ru/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### Повторное подписание манифестов приложения и развертывания с помощью mage.exe  
  
1.  Откройте окно **Командная строка Visual Studio**.  
  
2.  Измените папки на паки, содержащие файлы манифестов, которые необходимо подписать.  
  
3.  Введите следующую команду для подписания файла манифеста приложения.  Замените ManifestFileName именем файла манифеста с расширением.  Замените Certificate относительным или полным путем к файлу сертификата и замените Password паролем сертификата.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Например, для подписания манифеста приложения для надстройки, приложения Windows Form или браузерного приложения Windows Presentation Foundation следует выполнить следующую команду.  Временные сертификаты, созданные Visual Studio, не рекомендуется использовать при развертывании в рабочих средах.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Введите следующую команду для обновления и подписания файла манифеста развертывания. Для этого замените заполнители, как указано выше.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Например, чтобы обновить и подписать манифест развертывания для надстройки Excel, приложения Windows Forms или приложения браузера Windows Presentation Foundation, следует выполнить следующую команду.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Разработчик также может скопировать основной манифест развертывания \(publish\\*\<appname\>*.application\) в каталог развертывания версий \(publish\\Application Files\\*\<appname\>*\_*\<version\>*\).  
  
## Обновление и повторное подписание манифестов приложения и развертывания  
 В этой процедуре предполагается, что в файл манифеста приложения \(MANIFEST\) уже внесены изменения, но существуют другие файлы, которые были обновлены.  При обновлении файлов должен быть также обновлен хэш, представляющий файл.  
  
#### Обновление и повторное подписание манифестов приложения и развертывания с помощью Mage.exe  
  
1.  Откройте окно **Командная строка Visual Studio**.  
  
2.  Измените папки на паки, содержащие файлы манифестов, которые необходимо подписать.  
  
3.  Удалите расширение DEPLOY из файлов в папке выходных данных публикации.  
  
4.  Введите указанную ниже команду, чтобы обновить манифест приложения новыми хэшами для обновленных файлов и подписать файл манифеста приложения.  Замените ManifestFileName именем файла манифеста с расширением.  Замените Certificate относительным или полным путем к файлу сертификата и замените Password паролем сертификата.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Например, для подписания манифеста приложения для надстройки, приложения Windows Form или браузерного приложения Windows Presentation Foundation следует выполнить следующую команду.  Временные сертификаты, созданные Visual Studio, не рекомендуется использовать при развертывании в рабочих средах.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Введите следующую команду для обновления и подписания файла манифеста развертывания. Для этого замените заполнители, как указано выше.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Например, чтобы обновить и подписать манифест развертывания для надстройки Excel, приложения Windows Forms или приложения браузера Windows Presentation Foundation, следует выполнить следующую команду.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Верните в файлы расширение DEPLOY, кроме файлов приложения и манифеста развертывания.  
  
7.  Разработчик также может скопировать основной манифест развертывания \(publish\\*\<appname\>*.application\) в каталог развертывания версий \(publish\\Application Files\\*\<appname\>*\_*\<version\>*\).  
  
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
 [Практическое руководство. Настройка поведения запроса о доверии ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)