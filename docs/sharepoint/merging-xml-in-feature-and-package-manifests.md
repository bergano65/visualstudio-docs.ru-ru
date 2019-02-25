---
title: Слияние XML в компонентов и пакетов манифестах | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8af9386d192c6dd96669dbfada298317cf5fe0e5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646308"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Слияние XML в манифестах компонентов и пакетов
  Компоненты и пакеты определяются [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] файлов манифеста. Эти манифесты в пакете представляют собой сочетание данных, сформированных из конструкторов и пользовательского [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] введенного пользователем в шаблон манифеста. Во время упаковки [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] сливает пользовательские [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] инструкции с предоставляемыми конструктором [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] для формирования в пакете [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] файл манифеста. Одинаковые элементы, за исключением указанных далее в исключения слияния, объединяются во избежание [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ошибок проверки после развертывания файлов в SharePoint и сделать файл манифеста файлы становится компактнее и эффективнее.

## <a name="modify-the-manifests"></a>Изменение манифестов
 Нельзя напрямую изменять файла манифеста в пакете, пока вы не отключите конструкторы компонента или пакета. Тем не менее, можно вручную добавить пользовательские [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] элементов шаблон манифеста через конструкторы компонентов и пакетов или [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] редактора. Дополнительные сведения см. в разделе [Как Настройка компонента SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) и [как: Настройка пакета решения SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

## <a name="feature-and-package-manifest-merge-process"></a>Процесс слияния манифестов компонентов и пакетов
 При объединении пользовательских элементов с элементами, предоставляемыми конструктором, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] использует следующий процесс. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] проверяет, имеет ли каждый элемент уникальное значение ключа. Если элемент не имеет уникального значения ключа, он добавляется в файл манифеста пакета. Аналогично, элементы с несколькими ключами не могут быть объединены. Таким образом они добавляются в файл манифеста.

 Если элемент имеет уникальный ключ, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] сравнивает значения конструктора и пользовательские ключи. Если значения совпадают, они выполняют слияние в одно значение. Если значения не совпадают, значение ключа конструктора не учитывается, и используется значение пользовательского ключа. Коллекции также объединяются. Например если сформированный конструктором [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] и пользовательский [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] оба содержат коллекцию сборок, упакованного манифеста содержит только одну коллекцию сборок.

## <a name="merge-exceptions"></a>Исключения слияния
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] объединяет большинство конструктор [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] элементов вместе с аналогичной пользовательской [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] элементов, если они имеют один, уникальный идентифицирующий атрибут. Однако у некоторых элементов отсутствует уникальный идентификатор, необходимый для [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] слияния. Эти элементы называются *исключения слияния*. В этих случаях [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] объединяет пользовательские [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] элементов вместе с предоставляемыми конструктором [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] элементов, но добавляет их в файл манифеста в пакете.

 Ниже приведен список исключений слияния для компонентов и пакетов [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] файлов манифеста.

|Designer|XML-элемент|
|--------------|-----------------|
|Конструктор компонентов|ActivationDependency|
|Конструктор компонентов|UpgradeAction|
|Конструктор пакетов|SafeControl|
|Конструктор пакетов|CodeAccessSecurity|

## <a name="feature-manifest-elements"></a>Элементы манифеста компонента
 Ниже приведен список всех элементов манифеста компонентов, которые могут быть объединены и их уникальный ключ, который используется для сопоставления.

|Имя элемента|Уникальный ключ|
|------------------|----------------|
|Компонент (все атрибуты)|*Имя атрибута* (каждое имя атрибута элемента компонента является уникальным ключом).|
|ElementFile|Расположение|
|ElementManifests/ElementManifest|Расположение|
|Свойство Properties /|Ключ|
|CustomUpgradeAction|name|
|CustomUpgradeActionParameter|name|

> [!NOTE]
>  Поскольку единственный способ изменить элемент CustomUpgradeAction в настраиваемом [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] редактора, эффект слияния не мал.

## <a name="package-manifest-elements"></a>Элементы манифеста пакета
 Ниже приведен список всех элементов манифеста пакета, которые могут быть объединены и их уникальный ключ, который используется для сопоставления.

|Имя элемента|Уникальный ключ|
|------------------|----------------|
|Решение (все атрибуты)|*Имя атрибута* (каждое имя атрибута элемента решения является уникальным ключом).|
|ApplicationResourceFiles/ApplicationResourceFile|Расположение|
|Сборки и сборки|Расположение|
|ClassResources/classresource:|Расположение|
|DwpFiles/DwpFile:|Расположение|
|FeatureManifests/FeatureManifest|Расположение|
|И ресурсов|Расположение|
|RootFiles/RootFile|Расположение|
|SiteDefinitionManifests/SiteDefinitionManifest|Расположение|
|WebTempFile|Расположение|
|TemplateFiles/TemplateFile|Расположение|
|SolutionDependency|SolutionID|

## <a name="manually-add-deployed-files"></a>Добавление развернутых файлов вручную
 Некоторые элементы манифеста, такие как ApplicationResourceFile и DwpFiles, укажите расположение, которое включает имя файла. Однако добавление записи имени файла в шаблон манифеста не добавляет базовый файл в пакет. Необходимо добавить файл к проекту, чтобы включить его в пакет и установите его свойство типа развертывания, соответствующим образом.

## <a name="see-also"></a>См. также
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Сборка и отладка решений SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
