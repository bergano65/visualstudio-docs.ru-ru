---
title: "Слияние XML в манифестах компонентов и пакетов | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "разработка приложений SharePoint в Visual Studio, упаковка"
ms.assetid: fc1cbd2a-0166-4f2f-a81b-4dac2fa7b0f3
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Слияние XML в манифестах компонентов и пакетов
  Компоненты и пакеты определяются файлами манифеста [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)].  Эти манифесты в пакете представляют собой комбинацию данных, сформированных из конструкторов и пользовательского [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)], введенного пользователем в шаблон манифеста.  Во время упаковки [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] сливает пользовательские операторы [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] с предоставляемыми конструктором [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] для формирования в пакете файла манифеста [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)].  Одинаковые элементы, за исключением указанных дальше в "Исключениях из слияния", сливаются, чтобы избежать проверки ошибок [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] после развертывания файлов в SharePoint и сделать файл манифеста более маленьким и эффективным.  
  
## Изменение манифестов  
 Пока не выключен конструктор компонентов или пакетов, нельзя непосредственно изменять файла манифеста в пакете.  Однако вручную в шаблон манифеста можно добавить пользовательские элементы [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] посредством конструктора компонентов или пакетов, или редактора [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)].  Дополнительные сведения см. в разделах [Практическое руководство. Настройка компонента SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) и [Практическое руководство. Настройка пакета решения SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## Процесс слияния манифестов компонентов и пакетов  
 При комбинировании пользовательских элементов с элементами, предоставляемыми конструктором, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] использует следующий процесс.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] проверяет уникальность ключа каждого элемента.  Если элемент не имеет уникального значения ключа, он добавляется в файл манифеста пакета.  Аналогично, элементы с несколькими ключи не могут быть объединены.  Таким образом они добавляются в файл манифеста.  
  
 Если элемент имеет уникальный ключ, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] сравнивает значения ключа конструктора и пользовательского ключа.  При совпадении значений, они сливаются в одно.  Если значения различны, значение ключа конструктора отбрасывается, а используется значение пользовательского ключа.  Коллекции также сливаются.  Например, если сформированный конструктором [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] и пользовательский [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] содержат коллекцию "Сборки", в упакованный манифест войдет только одна коллекция "Сборки".  
  
## Исключения слияния  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] сливает большинство элементов [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] конструктора с аналогичными пользовательскими элементами [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)], поскольку у них один, уникальный определяющий атрибут.  Однако у некоторых элементов отсутствует уникальный идентификатор, необходимый для слияния [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)].  Эти элементы известны как *исключения слияния*.  В этом случае [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] не объединяет пользовательские элементы [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] с элементами [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)], предоставляемыми конструктором, но добавляет их в файл манифеста в пакете.  
  
 Ниже приведен список исключений слияния для файлов манифеста компонентов и пакетов [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)].  
  
|Конструктор|XML\-элемент|  
|-----------------|------------------|  
|Конструктор компонентов|ActivationDependency|  
|Конструктор компонентов|UpgradeAction|  
|Конструктор пакетов|SafeControl|  
|Конструктор пакетов|CodeAccessSecurity|  
  
## Элементы манифеста компонентов  
 В следующей таблице приведен список всех элементов манифеста компонентов, которые можно слить, и их уникальные ключи, используемые для выявления соответствий.  
  
|Имя элемента|Уникальный ключ|  
|------------------|---------------------|  
|Компонент \(все атрибуты\)|*Attribute Name* \(Каждое имя атрибута элемента компонента является уникальным ключом\).|  
|ElementFile|Расположение|  
|ElementManifests\/ElementManifest|Расположение|  
|Свойства\/Свойство|Ключ|  
|CustomUpgradeAction|Имя|  
|CustomUpgradeActionParameter|Имя|  
  
> [!NOTE]  
>  Поскольку единственный способ изменить элемент CustomUpgradeAction заключается в использовании пользовательского редактора [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)], возможность не слияния достаточно низкая.  
  
## Элементы манифеста пакета  
 В следующей таблице приведен список всех элементов манифеста пакетов, которые можно слить, и их уникальные ключи, используемые для выявления соответствий.  
  
|Имя элемента|Уникальный ключ|  
|------------------|---------------------|  
|Решение \(все атрибуты\)|*Attribute Name* \(Каждое имя атрибута элемента "Решение" является уникальным ключом\).|  
|ApplicationResourceFiles\/ApplicationResourceFile|Расположение|  
|Сборки\/сборка|Расположение|  
|ClassResources\/ClassResource|Расположение|  
|DwpFiles\/DwpFile|Расположение|  
|FeatureManifests\/FeatureManifest|Расположение|  
|Ресурсы\/ресурс|Расположение|  
|RootFiles\/RootFile|Расположение|  
|SiteDefinitionManifests\/SiteDefinitionManifest|Расположение|  
|WebTempFile|Расположение|  
|TemplateFiles\/TemplateFile|Расположение|  
|SolutionDependency|SolutionID|  
  
## Добавление развернутых файлов вручную  
 Некоторые элементы манифеста, такие как ApplicationResourceFile и DwpFiles, указывают расположение, содержащее имя файла.  Однако добавление записи имени файла в шаблон манифеста не добавит указанный файл в пакет.  Файл необходимо добавить в проект, чтобы включить его в пакет, и соответствующим образом задать его свойство "Тип развертывания".  
  
## См. также  
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Построение и отладка решений SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  