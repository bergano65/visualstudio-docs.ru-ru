---
title: 'Layer Diagrams: Reference | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dd2b2d19e55cbaf9af63ddeafdbdf9f6d677c5bc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301609"
---
# <a name="layer-diagrams-reference"></a>Схемы слоев: справочные материалы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can use a *layer diagram* to visualize the high-level, logical architecture of your system. A layer diagram organizes the physical artifacts in your system into logical, abstract groups called *layers*. Слои описывают основные компоненты системы или задачи, выполняемые этими артефактами. Каждый слой может также содержать вложенные слои, описывающие более подробные задачи.

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Между слоями можно установить предполагаемые или существующие зависимости. Эти зависимости, представленные в виде стрелок, показывают, какие слои могут использовать или в настоящее время используют функциональные возможности, представленные другими слоями. Упорядочивая системы в слои, описывающие различные роли и функции, схемы слоев помогают изучать, повторно использовать и обслуживать код.

 С помощью схемы слоев можно также выполнять следующие задачи:

- представлять существующую или предполагаемую логическую архитектуру системы;

- выявлять конфликты между существующим кодом и предполагаемой архитектурой;

- визуализировать влияние изменений на предполагаемую архитектуру при рефакторинге, обновлении или развитии системы;

- дополнительно контролировать предполагаемую архитектуру в процессе разработки и обслуживания кода за счет добавления проверки операций возврата и построения.

  В этом разделе описаны элементы, которые можно использовать на схемах слоев. For more detailed information about how to create and draw layer diagrams, see [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md). For more information about layering patterns, visit the [Patterns & Practices site](https://go.microsoft.com/fwlink/?LinkId=145794).

## <a name="reading-layer-diagrams"></a>Чтение схем слоев
 ![Elements on layer diagrams](../modeling/media/uml-layerrefreading.png "UML_LayerRefReading")

 В следующей таблице описаны элементы, которые можно использовать на схемах слоев.

|**Shape**|**Элемент**|**Описание**|
|---------------|-----------------|---------------------|
|1|**Layer**|Логическая группа физических артефактов в системе. Артефактами могут быть пространства имен, проекты, классы, методы и т. п.<br /><br /> To see the artifacts that are linked to a layer, open the shortcut menu for the layer, and then choose **View Links** to open **Layer Explorer**.<br /><br /> For more information, see [Layer Explorer](#Explorer).<br /><br /> -   **Forbidden Namespace Dependencies** - Specifies that artifacts associated with this layer cannot depend on the specified namespaces.<br />-   **Forbidden Namespaces** - Specifies that artifacts associated with this layer must not belong to the specified namespaces.<br />-   **Required Namespaces** - Specifies that artifacts associated with this layer must belong to one of the specified namespaces.|
|2|**Dependency**|Указывает, что один слой может использовать функции другого слоя, но не наоборот.<br /><br /> -   **Direction** - Specifies the direction of the dependency.|
|3|**Bidirectional Dependency**|Указывает, что один слой может использовать функции другого слоя и наоборот.<br /><br /> -   **Direction** - Specifies the direction of the dependency.|
|4|**Комментарий**|Используется для добавления общих примечаний к схеме или ее элементам.|
|5|**Comment Link**|Используется для связи комментариев с элементами на схеме.|

## <a name="Explorer"></a> Layer Explorer
 Каждый слой можно связать с артефактами в решении, например с проектами, классами, пространствами имен, файлами проекта и другими частями программного обеспечения. Число на слое обозначает количество связанных с этим слоем артефактов. Число артефактов в слое следует толковать с учетом следующих факторов.

- Если слой связан с артефактом, содержащим другие артефакты, но слой не связан с другими артефактами напрямую, то число включает только связанный артефакт. Однако для анализа в ходе проверки слоя включаются другие артефакты.

   Например, если слой связан с одним пространством имен, то число связанных артефактов равно 1, даже если пространство имен содержит классы. Если слой также связан с каждым классом в пространстве имен, то число будет включать эти связанные классы.

- Если слой содержит другие слои, связанные с артефактами, то слой-контейнер также связан с этими артефактами, даже если число в слое-контейнере не включает эти артефакты.

  Дополнительные сведения о связывании слоев и артефактов см. в разделах:

- [Схемы слоев: рекомендации](../modeling/layer-diagrams-guidelines.md)

- [Создание схем слоев на основе кода](../modeling/create-layer-diagrams-from-your-code.md)

#### <a name="to-examine-the-linked-artifacts"></a>Просмотр связанных артефактов

- On the layer diagram, open the shortcut menu for one or more layers, and then choose **View Links**.

     **Layer Explorer** opens and shows the artifacts that are linked to the selected layers. **Layer Explorer** has a column that shows each of the properties of the artifact links.

    > [!NOTE]
    > If you cannot see all of these properties, expand the **Layer Explorer** window.

    |**Column in Layer Explorer**|**Описание**|
    |----------------------------------|---------------------|
    |**Categories**|Вид артефакта, например класс, пространство имен, исходный файл и т. д.|
    |**Layer**|Связанный с артефактом слой|
    |**Supports Validation**|If **True**, then the layer validation process can verify that the project conforms to dependencies to or from this element.<br /><br /> If **False**, then the link does not participate in the layer validation process.<br /><br /> For more information, see [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md).|
    |**Идентификатор**|Ссылка на связанный артефакт|

## <a name="see-also"></a>См. также раздел
 [Создание моделей для приложения](../modeling/create-models-for-your-app.md)
