---
title: Как добавить узлы в рабочую область из обозревателя XML-схем | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e0c8fe9d5ba8c096a03de7a9df85945f4aeb4a0a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656346"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Как добавлять узлы в рабочую область в обозревателе XML-схем
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе описывается добавление узлов в [рабочую область конструктора схем XML](../xml-tools/xml-schema-designer-workspace.md) из обозревателя XML-схем. Цель может быть достигнута посредством перетаскивания узлов из обозревателя XML-схемы на представление конструктора XSD, или использованием контекстного меню обозревателя XML-схем. Можно также добавить узлы, выделенные в результате поиска, выполненного в обозревателе XML-схем. Дополнительные сведения см. в разделе [как добавить в рабочую область узлы результатов поиска набора схем](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> В [рабочую область конструктора схем XML](../xml-tools/xml-schema-designer-workspace.md)можно добавлять только глобальные узлы.

### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Добавление узла посредством контекстного меню обозревателя XML

1. Выполните действия, описанные в разделе [Создание и изменение файла XSD-схемы](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. В обозревателе XSD щелкните правой кнопкой мыши узел `PurchaseOrderType`. Выберите **Показать в представлении графика**.

     Узел `purchaseOrderType` будет отображен в области конструктора в представлении графиков.

### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Перетаскивание узла на представление

1. В представлении графика щелкните правой кнопкой мыши узел `PurchaseOrderType`. Выберите команду " **отобразить" в обозревателе XML-схем**.

     Узел будет выделен в обозревателе XML-схем.

2. Щелкните правой кнопкой мыши узел `PurchaseOrderType` в обозревателе XML-схем и выберите пункт **отобразить все ссылки**.

     Узел `purchaseOrder` выделен.

3. Перетащите узел `purchaseOrder` в представление графика.

     Узел `purchaseOrder` и узел `PurchaseOrderType` будут отображены рядом друг с другом в области конструктора в представлении графиков. Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.

### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Добавление узлов с использованием возможностей поиска обозревателя схем

1. Введите "purchaseOrder" в текстовом поле "Поиск" на панели инструментов [проводника XML](../xml-tools/xml-schema-explorer.md) и нажмите кнопку "Поиск".

     ![Поиск ключевых слов обозревателя XML-схем](../xml-tools/media/schemaexplorersearch.gif "счемаексплорерсеарч")

     Результаты поиска также выделяются в обозревателе XML-схем и отмечаются галочками на вертикальной полосе прокрутки.

2. Добавьте результаты поиска в рабочую область, нажав кнопку **Добавить выделенные узлы в рабочую область** на панели сводки результатов.

     ![Результаты поиска в обозревателе XML-схем](../xml-tools/media/schemaexplorersearchresult.gif "счемаексплорерсеарчресулт")

     Узел `purchaseOrder` и узел `PurchaseOrderType` отображаются рядом друг с другом в области конструктора [представления графа](../xml-tools/graph-view.md). Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.

## <a name="see-also"></a>См. также раздел
 [Обозреватель схемы XML](../xml-tools/xml-schema-explorer.md)
