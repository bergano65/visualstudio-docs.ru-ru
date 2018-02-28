---
title: "Слияние XML в компонентов и пакетов манифесты | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 81e6f83dd4fc825e885843a47d45485918f7dabe
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="merging-xml-in-feature-and-package-manifests"></a>Слияние XML в манифестах компонентов и пакетов
  Компоненты и пакеты определяются [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] файлов манифеста. Эти манифесты в пакете представляют собой комбинацию данных, сформированных из конструкторов и пользовательского [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] введенного пользователем в шаблон манифеста. Во время упаковки [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] сливает пользовательские [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] инструкции с предоставляемыми конструктором [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] для формирования в пакете [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] файл манифеста. Одинаковые элементы, за исключением указанных далее в исключения слияния, объединяются во избежание [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ошибок проверки после развертывания файлов в SharePoint и сделать файл манифеста файлы компактный и эффективный.  
  
## <a name="modifying-the-manifests"></a>Изменение манифестов  
 Нельзя непосредственно изменять файла манифеста в пакете, пока вы не отключите конструкторы компонента или пакета. Тем не менее, можно вручную добавить пользовательские [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] элементов шаблон манифеста либо с помощью конструкторов компонентов и пакетов или [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] редактора. Дополнительные сведения см. в разделе [как: Настройка компонента SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) и [как: Настройка пакета решения SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## <a name="feature-and-package-manifest-merge-process"></a>Процесс слияния манифестов компонентов и пакетов  
 При комбинировании пользовательских элементов с элементами, предоставляемыми конструктором, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] использует следующую процедуру. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]проверяет, имеет ли каждый элемент уникальности значения ключа. Если элемент не имеет уникального значения ключа, он добавляется в файл манифеста пакета. Аналогично, элементы с несколькими ключами не могут быть объединены. Таким образом они добавляются в файл манифеста.  
  
 Если элемент имеет уникальный ключ, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] сравнивает значения конструктора и пользовательского ключа. Если значения совпадают, они выполняют слияние в одно значение. Если значения различаются, значение ключа конструктора отбрасывается и используется значение пользовательского ключа. Коллекции также объединяются. Например если сформированный конструктором [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] и пользовательский [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] оба содержат коллекцию сборок, упакованный манифест содержит только одну коллекцию сборок.  
  
## <a name="merge-exceptions"></a>Исключения слияния  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]объединяет большинство конструктор [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] элементы с аналогичными пользовательскими [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] элементов при условии, что у них один, уникальный идентифицирующий атрибут. Однако у некоторых элементов отсутствует уникальный идентификатор, необходимый для [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] слияния. Эти элементы называются *исключения слияния*. В этих случаях [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] объединяет пользовательские [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] элементов вместе с предоставляемыми конструктором [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] элементов, но добавляет их в файл манифеста в пакете.  
  
 Ниже приведен список исключений слияния для компонентов и пакетов [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] файлов манифеста.  
  
|Designer|XML-элемент|  
|--------------|-----------------|  
|Конструктор компонентов|ActivationDependency|  
|Конструктор компонентов|UpgradeAction|  
|Конструктор пакетов|SafeControl|  
|Конструктор пакетов|CodeAccessSecurity|  
  
## <a name="feature-manifest-elements"></a>Элементы манифеста компонента  
 Ниже приведен список всех элементов манифеста компонентов, которые могут быть объединены и их уникальный ключ, используемый для сопоставления.  
  
|Имя элемента|Уникальный ключ|  
|------------------|----------------|  
|Компонент (все атрибуты)|*Имя атрибута* (каждое имя атрибута элемента компонента является уникальным ключом).|  
|ElementFile|Расположение|  
|ElementManifests или манифест элемента|Расположение|  
|Свойства и свойства|Ключ|  
|CustomUpgradeAction|name|  
|CustomUpgradeActionParameter|name|  
  
> [!NOTE]  
>  Поскольку единственный способ изменить элемент CustomUpgradeAction в пользовательских [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] редактора, эффект слияния не недостаточно.  
  
## <a name="package-manifest-elements"></a>Элементы манифеста пакета  
 Ниже приведен список всех элементов манифеста пакета, которые могут быть объединены и их уникальный ключ, используемый для сопоставления.  
  
|Имя элемента|Уникальный ключ|  
|------------------|----------------|  
|Решение (все атрибуты)|*Имя атрибута* (каждое имя атрибута элемента решения является уникальным ключом).|  
|ApplicationResourceFiles/ApplicationResourceFile|Расположение|  
|Сборки и сборки|Расположение|  
|ClassResources/ClassResource|Расположение|  
|DwpFiles/DwpFile|Расположение|  
|FeatureManifests/FeatureManifest|Расположение|  
|Ресурсы или ресурс|Расположение|  
|RootFiles/RootFile|Расположение|  
|SiteDefinitionManifests/SiteDefinitionManifest|Расположение|  
|WebTempFile|Расположение|  
|TemplateFiles/TemplateFile|Расположение|  
|SolutionDependency|SolutionID|  
  
## <a name="manually-add-deployed-files"></a>Добавление развернутых файлов вручную  
 Некоторые элементы манифеста, такие как ApplicationResourceFile и DwpFiles, укажите расположение, включающий имя файла. Однако добавление записи имени файла в шаблон манифеста не создается базовый файл пакета. Необходимо добавить файл в проект, чтобы включить его в пакет и установите его свойство типа развертывания соответствующим образом.  
  
## <a name="see-also"></a>См. также  
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Построение и отладка решений SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  