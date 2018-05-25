---
title: Добавить узлы результат поиска набора схем XML в рабочую область
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f6629aef7549a78f7cfdb73bb6d7ee0be3ac7412
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Способ: добавить узлы результат поиска набора схем в рабочую область

В этом разделе объясняется, как добавить узлы, которые выделены в **обозреватель XML-схем** в результате поиска по ключевому слову в рабочей области.

> [!NOTE]
> Можно добавлять только глобальные узлы для [рабочей](../xml-tools/xml-schema-designer-workspace.md).


 В этом примере используется образец [схема заказа на покупку](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Добавление результирующих узлов набора схем

1.  Следуйте указаниям в [как: Создание и изменение файла XSD-схемы](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  В текстовом поле поиска введите «purchaseOrder» [обозреватель XML](../xml-tools/xml-schema-explorer.md) панель инструментов и нажмите кнопку поиска.

     ![Поиск по ключевому слову обозреватель схемы XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     Результаты поиска выделяются цветом **обозреватель XML-схем** и отмечаются галочками на вертикальной полосе прокрутки.

3.  Добавить результаты поиска в рабочую область, щелкнув **Добавить выделенные узлы в рабочую область** кнопку на панели сводных результатов.

     ![Результаты поиска в обозревателе схемы XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     `purchaseOrder` Узла и `PurchaseOrderType` узла отображаются рядом друг с другом в области конструктора на [представление графика](../xml-tools/graph-view.md). Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.