---
title: Как добавлять узлы в рабочую область в обозревателе XML-схем
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e1f5821d3a4207d89eb62b9344cff967c73b536
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752057"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Как: добавлять узлы в рабочую область из обозревателя XML-схем

В этом разделе объясняется, как добавить узлы в [рабочей области конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md) из **обозреватель XML-схем**. Это можно сделать с помощью перетаскивания узлов из **обозреватель XML-схем** на представление конструктора XSD, либо с помощью **обозреватель XML-схем** контекстного меню. Можно также добавить узлы, выделенные в результате поиска, выполненного **обозреватель XML-схем**. Дополнительные сведения см. в разделе [как: добавить узлы результат поиска набора схем в рабочую область](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Можно добавлять только глобальные узлы для [рабочей области конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md).

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Добавление узла посредством контекстного меню обозревателя XML

1.  Следуйте указаниям в [как: Создание и изменение файла XSD-схемы](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Щелкните правой кнопкой мыши `PurchaseOrderType` узел в обозревателе XSD. Выберите **Показать в представлении графика**.

     Узел `purchaseOrderType` будет отображен в области конструктора в представлении графиков.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Перетаскивание узла на представление

1.  Щелкните правой кнопкой мыши `PurchaseOrderType` узел в представлении графика. Выберите **Показать в обозревателе XML-схем**.

     Узел будет выделен в **обозреватель XML-схем**.

2.  Щелкните правой кнопкой мыши `PurchaseOrderType` узел в **обозреватель XML-схем** и выберите **Показать все ссылки**.

     Узел `purchaseOrder` выделен.

3.  Перетащите узел `purchaseOrder` в представление графика.

     Узел `purchaseOrder` и узел `PurchaseOrderType` будут отображены рядом друг с другом в области конструктора в представлении графиков. Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Добавление узлов с использованием возможностей поиска обозревателя схем

1.  В текстовом поле поиска введите «purchaseOrder» [обозреватель XML](../xml-tools/xml-schema-explorer.md) панель инструментов и нажмите кнопку поиска.

     ![Поиск по ключевым словам в обозревателе схемы XML](../xml-tools/media/schemaexplorersearch.gif)

     Результаты поиска выделяются цветом **обозреватель XML-схем** и отмечаются галочками на вертикальной полосе прокрутки.

2.  Добавить результаты поиска в рабочую область, щелкнув **Добавить выделенные узлы в рабочую область** кнопку на панели сводных результатов.

     ![Результат поиска в обозревателе схемы XML](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder` Узла и `PurchaseOrderType` узла отображаются рядом друг с другом в области конструктора на [представление графика](../xml-tools/graph-view.md). Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.

## <a name="see-also"></a>См. также

- [Обозреватель схемы XML](../xml-tools/xml-schema-explorer.md)