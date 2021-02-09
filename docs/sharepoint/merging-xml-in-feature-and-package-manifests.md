---
title: Слияние XML в манифестах компонентов и пакетов | Документация Майкрософт
description: Созданный конструктором слиянием и добавленный пользователем XML-код в манифестах компонентов и пакетов SharePoint. Изучите элементы манифеста компонентов и пакетов, а затем объедините исключения.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8be6adfedeabaea236e4dcb2cd969e6023a7f3ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889568"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Слияние XML в манифестах компонентов и пакетов
  Компоненты и пакеты определяются [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] файлами манифеста. Эти Упакованные манифесты представляют собой сочетание данных, созданных из конструкторов, и пользовательских элементов, [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] вводимых в шаблон манифеста пользователями. Во время упаковки выполняет [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Слияние пользовательских [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] инструкций с предоставленным конструктором [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] для формирования упакованного [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] файла манифеста. Аналогичные элементы, с исключениями, упомянутыми позже в исключениях слияния, объединяются во избежание [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ошибок проверки после развертывания файлов в SharePoint, а также для повышения эффективности файлов манифеста.

## <a name="modify-the-manifests"></a>Изменение манифестов
 Невозможно напрямую изменить Упакованные файлы манифеста, пока не будут отключены конструкторы компонентов или пакетов. Однако можно вручную добавить пользовательские [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] элементы в шаблон манифеста с помощью конструкторов компонентов и пакетов или [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] редактора. Дополнительные сведения см. в разделе [как настроить компонент SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) и [как настроить пакет решения SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

## <a name="feature-and-package-manifest-merge-process"></a>Процесс слияния манифестов компонентов и пакетов
 При объединении пользовательских элементов вместе с элементами, предоставленными конструктором, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] использует следующий процесс. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] проверяет, имеет ли каждый элемент уникальное значение ключа. Если элемент не имеет уникального значения ключа, он добавляется в файл манифеста пакета. Аналогично, элементы с несколькими ключами не могут быть объединены. Поэтому они добавляются в файл манифеста.

 Если элемент имеет уникальный ключ, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] сравнивает значения конструктора и пользовательских ключей. Если значения совпадают, они объединяются в одно значение. Если значения различаются, значение ключа конструктора отбрасывается и используется значение пользовательского ключа. Коллекции также объединяются. Например, если созданный конструктором [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] и пользовательский элемент [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] содержат коллекцию Assemblies, упакованный манифест содержит только одну коллекцию сборок.

## <a name="merge-exceptions"></a>Объединить исключения
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] объединяет большинство элементов конструктора [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] вместе с аналогичными пользовательскими [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] элементами, если они имеют один уникальный идентифицирующий атрибут. Однако в некоторых элементах отсутствует уникальный идентификатор, необходимый для [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] объединения. Эти элементы называются *исключениями слияния*. В этих случаях не [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] объединяет пользовательские [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] элементы вместе с элементами, предоставленными конструктором [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] , но добавляет их в упакованный файл манифеста.

 Ниже приведен список исключений слияния для [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] файлов манифестов компонентов и пакетов.

|Designer|XML-элемент|
|--------------|-----------------|
|Конструктор компонентов|активатиондепенденци|
|Конструктор компонентов|упградеактион|
|Конструктор пакетов|SafeControl|
|Конструктор пакетов|кодеакцесссекурити|

## <a name="feature-manifest-elements"></a>Элементы манифеста компонентов
 В следующей таблице приведен список всех элементов манифеста компонентов, которые могут быть объединены, и их уникальный ключ, используемый для сопоставления.

|Имя элемента|Уникальный ключ|
|------------------|----------------|
|Функция (все атрибуты)|*Имя атрибута* (каждое имя атрибута элемента Feature является уникальным ключом).|
|ElementFile|Расположение|
|Елементманифестс/ElementManifest|Расположение|
|Свойства/свойство|Ключ|
|кустомупградеактион|Имя|
|кустомупградеактионпараметер|Имя|

> [!NOTE]
> Так как единственный способ изменить элемент Кустомупградеактион — в пользовательском [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] редакторе, результат не слияния невелик.

## <a name="package-manifest-elements"></a>Элементы манифеста пакета
 В следующей таблице приведен список всех элементов манифеста пакета, которые можно объединить, и их уникальный ключ, используемый для сопоставления.

|Имя элемента|Уникальный ключ|
|------------------|----------------|
|Решение (все атрибуты)|*Имя атрибута* (каждое имя атрибута элемента Solution является уникальным ключом).|
|Аппликатионресаурцефилес/Аппликатионресаурцефиле|Расположение|
|Сборки и сборки|Расположение|
|Классресаурцес/ClassResource|Расположение|
|Двпфилес/DwpFile|Расположение|
|Феатуреманифестс/Феатуреманифест|Расположение|
|Ресурсы/ресурс|Расположение|
|RootFiles/RootFile|Расположение|
|Ситедефинитионманифестс/Ситедефинитионманифест|Расположение|
|вебтемпфиле|Расположение|
|TemplateFiles/TemplateFile|Расположение|
|солутиондепенденци|SolutionID|

## <a name="manually-add-deployed-files"></a>Добавление развернутых файлов вручную
 Некоторые элементы манифеста, такие как Аппликатионресаурцефиле и Двпфилес, указывают расположение, содержащее имя файла. Однако добавление записи имени файла в шаблон манифеста не приводит к добавлению в пакет базового файла. Необходимо добавить файл в проект, чтобы включить его в пакет и задать соответствующее свойство для соответствующего типа развертывания.

## <a name="see-also"></a>См. также раздел
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Сборка и отладка решений SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
