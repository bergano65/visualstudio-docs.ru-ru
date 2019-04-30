---
title: Практическое руководство. Добавление узлов в рабочую область в обозревателе схем XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f38760e6a04bd9e88fd4ff6e8c9d31f30ba27647
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783258"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Практическое руководство. Добавление узлов в рабочую область в обозревателе схем XML

В этом разделе объясняется, как добавить узлы в [рабочей области конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md) из **обозреватель XML-схем**. Это можно сделать с помощью перетаскивания узлов из **обозреватель XML-схем** на представление конструктора XSD, или с помощью **обозреватель XML-схем** контекстного меню. Можно также добавить узлы, выделенные в результате поиска, выполненного **обозреватель XML-схем**. Дополнительные сведения см. в разделе [Как Добавить в рабочую область узлы результат поиска набора схем](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Только глобальные узлы, которые могут добавляться к [рабочей области конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md).

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Добавление узла посредством контекстного меню обозревателя XML

1. Выполните действия, описанные в [как: Создание и изменение файла схемы XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Щелкните правой кнопкой мыши `PurchaseOrderType` узел в обозревателе XSD. Выберите **Показать в представлении графика**.

     Узел `purchaseOrderType` будет отображен в области конструктора в представлении графиков.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Перетаскивание узла на представление

1. Щелкните правой кнопкой мыши `PurchaseOrderType` узел в представлении графика. Выберите **Показать в обозревателе XML-схем**.

     Узел будет выделен в **обозреватель XML-схем**.

2. Щелкните правой кнопкой мыши `PurchaseOrderType` узел в **обозреватель XML-схем** и выберите **Показать все ссылки**.

     Узел `purchaseOrder` выделен.

3. Перетащите узел `purchaseOrder` в представление графика.

     Узел `purchaseOrder` и узел `PurchaseOrderType` будут отображены рядом друг с другом в области конструктора в представлении графиков. Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Добавление узлов с использованием возможностей поиска обозревателя схем

1. В текстовом поле поиска введите «purchaseOrder» [обозреватель XML](../xml-tools/xml-schema-explorer.md) панель инструментов и нажмите кнопку поиска.

     ![Поиск по ключевым словам в обозревателе схемы XML](../xml-tools/media/schemaexplorersearch.gif)

     Результаты поиска выделяются цветом **обозреватель XML-схем** и отмечаются галочками на вертикальной полосе прокрутки.

2. Добавить результаты поиска в рабочую область, щелкнув **Добавить выделенные узлы в рабочую область** кнопку на панели сводных результатов.

     ![Результат поиска в обозревателе схемы XML](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder` Узла и `PurchaseOrderType` узел отображаться рядом друг с другом в области конструктора [представление графика](../xml-tools/graph-view.md). Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.

## <a name="see-also"></a>См. также

- [Обозреватель схемы XML](../xml-tools/xml-schema-explorer.md)