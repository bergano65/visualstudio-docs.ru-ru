---
title: Использование технологии ClickOnce для развертывания приложений multitarget
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 38418a1ca11c23ab12d64deadfb91079bc957493
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747485"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Практическое руководство. использование технологии ClickOnce для развертывания приложений, которые могут выполняться в нескольких версиях .NET Framework
Можно развернуть приложение, предназначенное для нескольких версий платформы .NET Framework с помощью технологии развертывания ClickOnce. Это требует создания и обновление манифестов приложения и развертывания.

> [!NOTE]
> Прежде чем устанавливать приложение на несколько версий платформы .NET Framework, следует убедиться, что приложение работает с несколькими версиями платформы .NET Framework. Среда CLR версии отличается от .NET Framework 4 и .NET Framework 2.0, .NET Framework 3.0 и .NET Framework 3.5.

 Этот процесс включает следующие шаги:

1. Создание манифестов приложения и развертывания.

2. Включение нескольких версий платформы .NET Framework в манифест развертывания.

3. Изменение *app.config* файл, чтобы получить список совместимых версий среды выполнения .NET Framework.

4. Изменения манифеста приложения для пометки зависимых сборок как сборок платформы .NET Framework.

5. Подпишите манифест приложения.

6. Обновить и подписать манифест развертывания.

### <a name="to-generate-the-application-and-deployment-manifests"></a>Для создания манифестов приложения и развертывания

- Используйте мастер публикации или страницы публикации в конструкторе проектов для публикации приложения и создания приложения и файлы манифеста развертывания. Дополнительные сведения см. в разделе [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) или [страницы публикации, конструктор проектов](../ide/reference/publish-page-project-designer.md).

### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Чтобы изменить манифест развертывания, чтобы получить список нескольких версий .NET Framework

1. В каталоге публикации откройте манифест развертывания с помощью редактора XML в Visual Studio. Манифест развертывания содержит *.application* расширение имени файла.

2. Замените XML-код между `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` и `</compatibleFrameworks>` элементы XML-кодом, перечислены поддерживаемые версии .NET Framework для вашего приложения.

     Ниже приведены некоторые доступные версии .NET Framework и соответствующий XML-код, который можно добавить в манифест развертывания.

    |Версия платформы .NET Framework|XML|
    |----------------------------|---------|
    |4 Client|\<Framework targetVersion = «4.0» profile = supportedRuntime «Клиент» = «4.0.30319 необходимо» / >|
    |4 Full|\<framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />|
    |3.5 Client|\<Framework targetVersion = «3.5» profile = supportedRuntime «Клиент» = «2.0.50727» / >|
    |3.5 Full|\<framework targetVersion="3.5" profile="Full" supportedRuntime="2.0.50727" />|
    |3.0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|

### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Чтобы изменить файл app.config, чтобы получить список совместимых версий среды выполнения .NET Framework

1. В обозревателе решений откройте *app.config* файл с помощью редактора XML в Visual Studio.

2. Замените (или добавьте) XML-код между `<startup>` и `</startup>` элементов при помощи XML со списком поддерживаемых сред выполнения .NET Framework, для вашего приложения.

     Ниже приведены некоторые доступные версии .NET Framework и соответствующий XML-код, который можно добавить в манифест развертывания.

    |Версия среды выполнения .NET framework|XML|
    |------------------------------------|---------|
    |4 Client|\<версия supportedRuntime = sku «v4.0.30319» =». NETFramework, версия = v4.0, профиль клиента =» / >|
    |4 Full|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0" />|
    |3.5 Full|\<supportedRuntime version="v2.0.50727"/>|
    |3.5 Client|\<supportedRuntime version="v2.0.50727" sku="Client"/>|

### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Для изменения манифеста приложения для пометки зависимых сборок как сборок платформы .NET Framework

1. В каталоге публикации откройте манифест приложения с помощью редактора XML в Visual Studio. Манифест развертывания содержит *.manifest* расширение имени файла.

2. Добавить `group="framework"` зависимость XML для отмеченных сборок (`System.Core`, `WindowsBase`, `Sentinel.v3.5Client`, и `System.Data.Entity`). Например XML-код должен выглядеть следующим образом:

   ```xml
   <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">
   ```

3. Обновить номер версии `<assemblyIdentity>` элемент для Microsoft.Windows.CommonLanguageRuntime номеру версии для платформы .NET Framework, который является наименьшим общим знаменателем. Например если приложение предназначено для .NET Framework 3.5 и .NET Framework 4, номер версии используйте 2.0.50727.0 и XML должен выглядеть следующим образом:

   ```xml
   <dependency>
     <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
       <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />
     </dependentAssembly>
   </dependency>
   ```

### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Обновление и повторное подписание приложения и развертывания манифестов

- Обновление и повторное подписание манифестов приложения и развертывания. Дополнительные сведения см. в разделе [Практическое руководство. повторно подписать манифесты приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>См. также
- [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)
- [\<compatibleFrameworks > элемент](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [\<зависимость > элемент](../deployment/dependency-element-clickonce-application.md)
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Схема файла конфигурации](/dotnet/framework/configure-apps/file-schema/index)
