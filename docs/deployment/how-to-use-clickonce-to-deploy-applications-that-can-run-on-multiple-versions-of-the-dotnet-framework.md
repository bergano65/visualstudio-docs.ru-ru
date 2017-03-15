---
title: "Практическое руководство. Использование технологии ClickOnce для развертывания приложений, которые могут выполняться в нескольких версиях .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "приложения ClickOnce, несколько версий платформы .NET Framework"
  - "развертывание ClickOnce, несколько версий платформы .NET Framework"
  - "развертывание приложений [ClickOnce], несколько версий платформы .NET Framework"
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Практическое руководство. Использование технологии ClickOnce для развертывания приложений, которые могут выполняться в нескольких версиях .NET Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Разработчик может развернуть приложение, предназначенное для нескольких версий платформы .NET Framework, с помощью технологии развертывания ClickOnce.  Для этого необходимо создать и обновить манифесты приложения и развертывания.  
  
> [!NOTE]
>  Так как приложение настраивается для работы в нескольких версиях платформы .NET Framework, необходимо убедиться в том, что приложение действительно может выполняться в различных версиях платформы.  Среда CLR в [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] отличается от среды в платформах .NET Framework 2.0, .NET Framework 3.0 и .NET Framework 3.5.  
  
 Данная процедура требует выполнения следующих действий:  
  
1.  Создание манифестов приложения и развертывания.  
  
2.  Включение нескольких версий платформы .NET Framework в манифест развертывания.  
  
3.  Добавление версий среды выполнения, совместимых с платформой .NET Framework, в файл app.config.  
  
4.  Изменение манифеста приложения для пометки зависимых сборок в качестве сборок платформы .NET Framework.  
  
5.  Подписание манифеста приложения.  
  
6.  Обновление и подписание обновленного манифеста развертывания.  
  
### Создание манифестов приложения и развертывания  
  
-   Используйте мастер публикации или страницу конструктора проектов "Публикация" для публикации приложения и создания файлов манифеста приложения и развертывания.  Дополнительные сведения см. в разделах [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md) или [Страница публикации в конструкторе проектов](../ide/reference/publish-page-project-designer.md).  
  
### Включение нескольких версий платформы .NET Framework в манифест развертывания  
  
1.  Отройте манифест развертывания в каталоге публикации с помощью редактора XML в Visual Studio.  Манифест развертывания имеет расширение APPLICATION.  
  
2.  Замените XML\-код между элементами `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` и `</compatibleFrameworks>` XML\-кодом, описывающим поддерживаемые в данном приложении версии платформы .NET Framework.  
  
     В следующей таблице приведены некоторые доступные версии платформы .NET Framework и соответствующий XML\-код, добавляемый в манифест развертывания.  
  
    |Версия платформы .NET Framework|XML|  
    |-------------------------------------|---------|  
    |4 клиентская|\<framework targetVersion\="4.0" profile\="Client" supportedRuntime\="4.0.30319" \/\>|  
    |4 полная|\<framework targetVersion\="4.0" profile\="Full" supportedRuntime\="4.0.30319" \/\>|  
    |3.5 клиентская|\<framework targetVersion\="3.5" profile\="Client" supportedRuntime\="2.0.50727" \/\>|  
    |3.5 полная|\<framework targetVersion\="3.5" profile\="Full" supportedRuntime\="2.0.50727" \/\>|  
    |3.0|\<framework targetVersion\="3.0" supportedRuntime\="2.0.50727" \/\>|  
  
### Добавление в файл app.config версий среды выполнения, совместимых с платформой .NET Framework  
  
1.  Откройте файл App.config в обозревателе решений с помощью редактора XML в Visual Studio.  
  
2.  Замените XML\-код между элементами `<startup>` и `</startup>` XML\-кодом, описывающим поддерживаемые в данном приложении версии сред выполнения платформы .NET Framework.  
  
     В следующей таблице приведены некоторые доступные версии платформы .NET Framework и соответствующий XML\-код, добавляемый в манифест развертывания.  
  
    |Версия среды выполнения для платформы .NET Framework|XML|  
    |----------------------------------------------------------|---------|  
    |4 клиентская|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0,Profile\=Client" \/\>|  
    |4 полная|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0" \/\>|  
    |3.5 полная|\<supportedRuntime version\="v2.0.50727"\/\>|  
    |3.5 клиентская|\<supportedRuntime version\="v2.0.50727" sku\="Client"\/\>|  
  
### Изменение манифеста приложения для пометки зависимых сборок в качестве сборок платформы .NET Framework  
  
1.  Откройте манифест приложения в каталоге публикации с помощью редактора XML в Visual Studio.  Манифест развертывания имеет расширение MANIFEST.  
  
2.  Добавьте элемент `group="framework"` в XML\-код зависимостей для отмеченных сборок \(`System.Core`, `WindowsBase`, `Sentinel.v3.5Client` и `System.Data.Entity`\).  Например, XML\-код может выглядеть следующим образом:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  Замените номер версии элемента `<assemblyIdentity>` для Microsoft.Windows.CommonLanguageRuntime номером версии платформы .NET Framework с наименьшим общим знаменателем.  Например, если приложение предназначено для платформ .NET Framework 3.5 и [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)], следует использовать номер версии 2.0.50727.0, а XML\-код должен выглядеть следующим образом:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### Обновление и повторное подписание манифестов приложения и развертывания  
  
-   Обновите и повторно подпишите манифесты приложения и развертывания.  Дополнительные сведения см. в разделе [Практическое руководство. Повторное подписание манифестов приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## См. также  
 [Публикация ClickOnce\-приложений](../deployment/publishing-clickonce-applications.md)   
 [Элемент \<compatibleFrameworks\>](../Topic/%3CcompatibleFrameworks%3E%20Element%20\(ClickOnce%20Deployment\).md)   
 [Элемент \<dependency\>](../deployment/dependency-element-clickonce-application.md)   
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Схема файла конфигурации](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)