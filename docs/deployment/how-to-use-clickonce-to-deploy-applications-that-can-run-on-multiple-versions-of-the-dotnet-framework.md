---
title: 'Как: использовать ClickOnce для развертывания приложения, работающие на нескольких версиях платформы .NET Framework | Документы Microsoft'
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
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 310f6a25dd0729845c2b5b6d6432f2027038780b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Практическое руководство. Использование технологии ClickOnce для развертывания приложений, которые могут выполняться в нескольких версиях .NET Framework
Можно развернуть приложение, предназначенное для нескольких версий платформы .NET Framework с помощью технологии развертывания ClickOnce. Требуется создать и обновить манифесты приложения и развертывания.  
  
> [!NOTE]
>  Прежде чем установить приложение на несколько версий платформы .NET Framework, следует убедиться, что приложение работает с несколькими версиями платформы .NET Framework. Версия общеязыковой отличается от [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] и .NET Framework 2.0, .NET Framework 3.0 и .NET Framework 3.5.  
  
 Этот процесс включает следующие шаги:  
  
1.  Создание манифестов приложения и развертывания.  
  
2.  Включение нескольких версий платформы .NET Framework в манифест развертывания.  
  
3.  Измените файл app.config, чтобы вывести список совместимых версий среды выполнения .NET Framework.  
  
4.  Изменение манифеста приложения для пометки зависимых сборок в качестве сборок платформы .NET Framework.  
  
5.  Подпишите манифест приложения.  
  
6.  Обновите и подпишите манифест развертывания.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>Создание манифестов приложения и развертывания  
  
-   Для публикации приложения и создания файлов манифеста развертывания приложения и используйте мастер публикации или страница публикации в конструкторе проектов. Дополнительные сведения см. в разделе [как: публикация приложения ClickOnce с использованием мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) или [страницы публикации, конструктор проектов](../ide/reference/publish-page-project-designer.md).  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Чтобы изменить манифест развертывания, чтобы Включение нескольких версий платформы .NET Framework  
  
1.  В каталоге публикации откройте манифест развертывания с помощью редактора XML в Visual Studio. Манифест развертывания имеет расширение имени файла приложения.  
  
2.  Замените код XML между `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` и `</compatibleFrameworks>` элементы XML-кодом, перечислены поддерживаемые версии .NET Framework для приложения.  
  
     Ниже приведены некоторые доступные версии платформы .NET Framework и соответствующий XML-код, который можно добавить в манифест развертывания.  
  
    |Версия платформы .NET Framework|XML|  
    |----------------------------|---------|  
    |4 клиента|\<Framework targetVersion = «4.0» профиль = supportedRuntime «Клиент» = «4.0.30319 необходимо» / >|  
    |4 full|\<Framework targetVersion = «4.0» профиль = «Full» supportedRuntime = «4.0.30319 необходимо» / >|  
    |3.5 клиента|\<Framework targetVersion = «3.5» профиль = supportedRuntime «Клиент» = «2.0.50727» / >|  
    |3.5 полный|\<Framework targetVersion = «3.5» профиль = «Full» supportedRuntime = «2.0.50727» / >|  
    |3.0|\<Framework targetVersion = «3.0» supportedRuntime = «2.0.50727» / >|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Чтобы изменить файл app.config, чтобы вывести список совместимых версий среды выполнения .NET Framework  
  
1.  В обозревателе решений откройте файл App.config с помощью редактора XML в Visual Studio.  
  
2.  Замените (или добавить) XML-кода между `<startup>` и `</startup>` элементы с XML, в которой перечислены поддерживаемые среды выполнения .NET Framework для приложения.  
  
     Ниже приведены некоторые доступные версии платформы .NET Framework и соответствующий XML-код, который можно добавить в манифест развертывания.  
  
    |Версия среды выполнения .NET framework|XML|  
    |------------------------------------|---------|  
    |4 клиента|\<версия supportedRuntime = sku «v4.0.30319» =». NETFramework, версия = версии 4.0, профиль клиента =» / >|  
    |4 full|\<версия supportedRuntime = sku «v4.0.30319» =». NETFramework, версия = v4.0» / >|  
    |3.5 полный|\<supportedRuntime version="v2.0.50727"/ >|  
    |3.5 клиента|\<supportedRuntime версия = «v2.0.50727» sku = «Client» / >|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Изменение манифеста приложения для пометки зависимых сборок в качестве сборок платформы .NET Framework  
  
1.  В каталоге публикации откройте манифест приложения с помощью редактора XML в Visual Studio. Манифест развертывания имеет расширение manifest.  
  
2.  Добавить `group="framework"` для XML-код зависимостей для отмеченных сборок (`System.Core`, `WindowsBase`, `Sentinel.v3.5Client`, и `System.Data.Entity`). Например XML-код должен выглядеть следующим образом:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  Обновить номер версии `<assemblyIdentity>` элемент для Microsoft.Windows.CommonLanguageRuntime номер версии платформы .NET Framework, начиная с самого общий знаменатель. Например, если приложение предназначено для .NET Framework 3.5 и [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)], используйте 2.0.50727.0 номер версии и XML должен выглядеть следующим образом:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Обновление и повторное подписание приложения и развертывания манифестов  
  
-   Обновление и повторное подписание манифестов приложения и развертывания. Для получения дополнительной информации см. [Практическое руководство. Повторное подписание манифестов приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>См. также  
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks > элемент](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<зависимость > элемент](../deployment/dependency-element-clickonce-application.md)   
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Схема файла конфигурации](/dotnet/framework/configure-apps/file-schema/index)