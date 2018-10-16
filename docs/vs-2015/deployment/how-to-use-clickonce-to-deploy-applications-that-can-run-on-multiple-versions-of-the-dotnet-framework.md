---
title: 'Практическое: использование технологии ClickOnce для развертывания приложений, которые могут выполняться на различных версиях платформы .NET Framework | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 7731526b09ab3014b9f3256ee1f4e4d0dd653a34
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259068"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Практическое руководство. Использование технологии ClickOnce для развертывания приложений, которые могут выполняться в нескольких версиях .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно развернуть приложение, предназначенное для нескольких версий платформы .NET Framework с помощью технологии развертывания ClickOnce. Это требует создания и обновление манифестов приложения и развертывания.  
  
> [!NOTE]
>  Прежде чем устанавливать приложение на несколько версий платформы .NET Framework, следует убедиться, что приложение работает с несколькими версиями платформы .NET Framework. Среда CLR версии отличается между [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] и .NET Framework 2.0, .NET Framework 3.0 и .NET Framework 3.5.  
  
 Этот процесс включает следующие шаги:  
  
1.  Создание манифестов приложения и развертывания.  
  
2.  Включение нескольких версий платформы .NET Framework в манифест развертывания.  
  
3.  Измените файл app.config, чтобы получить список совместимых версий среды выполнения .NET Framework.  
  
4.  Изменения манифеста приложения для пометки зависимых сборок как сборок платформы .NET Framework.  
  
5.  Подпишите манифест приложения.  
  
6.  Обновить и подписать манифест развертывания.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>Для создания манифестов приложения и развертывания  
  
-   Используйте мастер публикации или страницы публикации в конструкторе проектов для публикации приложения и создания приложения и файлы манифеста развертывания. Дополнительные сведения см. в разделе [как: публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) или [страницы публикации, конструктор проектов](../ide/reference/publish-page-project-designer.md).  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Чтобы изменить манифест развертывания, чтобы получить список нескольких версий .NET Framework  
  
1.  В каталоге публикации откройте манифест развертывания с помощью редактора XML в Visual Studio. Манифест развертывания имеет расширение имени файла приложения.  
  
2.  Замените XML-код между `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` и `</compatibleFrameworks>` элементы XML-кодом, перечислены поддерживаемые версии .NET Framework для вашего приложения.  
  
     Ниже приведены некоторые доступные версии .NET Framework и соответствующий XML-код, который можно добавить в манифест развертывания.  
  
    |Версия платформы .NET Framework|XML|  
    |----------------------------|---------|  
    |4 клиента|\<Framework targetVersion = «4.0» profile = supportedRuntime «Клиент» = «4.0.30319 необходимо» / >|  
    |4 full|\<Framework targetVersion = «4.0» profile = «Full» supportedRuntime = «4.0.30319 необходимо» / >|  
    |3.5 клиента|\<Framework targetVersion = «3.5» profile = supportedRuntime «Клиент» = «2.0.50727» / >|  
    |3.5 полный|\<Framework targetVersion = «3.5» profile = «Full» supportedRuntime = «2.0.50727» / >|  
    |3.0|\<Framework targetVersion = «3.0» supportedRuntime = «2.0.50727» / >|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Чтобы изменить файл app.config, чтобы получить список совместимых версий среды выполнения .NET Framework  
  
1.  В обозревателе решений откройте файл App.config с помощью редактора XML в Visual Studio.  
  
2.  Замените (или добавьте) XML-код между `<startup>` и `</startup>` элементов при помощи XML со списком поддерживаемых сред выполнения .NET Framework, для вашего приложения.  
  
     Ниже приведены некоторые доступные версии .NET Framework и соответствующий XML-код, который можно добавить в манифест развертывания.  
  
    |Версия среды выполнения .NET framework|XML|  
    |------------------------------------|---------|  
    |4 клиента|\<версия supportedRuntime = sku «v4.0.30319» =». NETFramework, версия = v4.0, профиль клиента =» / >|  
    |4 full|\<версия supportedRuntime = sku «v4.0.30319» =». NETFramework, версия = v4.0» / >|  
    |3.5 полный|\<supportedRuntime version="v2.0.50727"/ >|  
    |3.5 клиента|\<версия supportedRuntime = sku «v2.0.50727» = «Client» / >|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Для изменения манифеста приложения для пометки зависимых сборок как сборок платформы .NET Framework  
  
1.  В каталоге публикации откройте манифест приложения с помощью редактора XML в Visual Studio. Манифест развертывания имеет расширение manifest.  
  
2.  Добавить `group="framework"` зависимость XML для отмеченных сборок (`System.Core`, `WindowsBase`, `Sentinel.v3.5Client`, и `System.Data.Entity`). Например XML-код должен выглядеть следующим образом:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  Обновить номер версии `<assemblyIdentity>` элемент для Microsoft.Windows.CommonLanguageRuntime номеру версии для платформы .NET Framework, который является наименьшим общим знаменателем. Например, если приложение предназначено для .NET Framework 3.5 и [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)], номер версии используйте 2.0.50727.0 и XML должен выглядеть следующим образом:  
  
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
 [Схема файла конфигурации](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)



