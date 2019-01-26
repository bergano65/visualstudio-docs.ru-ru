---
title: Как выполнить Добавление узлов в рабочую область в обозревателе схем XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 699f57829e2f7d9bfd7a8841f5b1c82de5b9c7f7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012109"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Как выполнить Добавление узлов в рабочую область в обозревателе XML-схемы

В этом разделе объясняется, как добавить узлы в [рабочей области конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md) из **обозреватель XML-схем**. Это можно сделать с помощью перетаскивания узлов из **обозреватель XML-схем** на представление конструктора XSD, или с помощью **обозреватель XML-схем** контекстного меню. Можно также добавить узлы, выделенные в результате поиска, выполненного **обозреватель XML-схем**. Дополнительные сведения см. в разделе [Как Добавить в рабочую область узлы результат поиска набора схем](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Только глобальные узлы, которые могут добавляться к [рабочей области конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md).

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Добавление узла посредством контекстного меню обозревателя XML

1.  Выполните действия, описанные в [как: Создание и изменение файла схемы XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

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

     `purchaseOrder` Узла и `PurchaseOrderType` узел отображаться рядом друг с другом в области конструктора [представление графика](../xml-tools/graph-view.md). Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.

## <a name="see-also"></a>См. также

- [Обозреватель схемы XML](../xml-tools/xml-schema-explorer.md)