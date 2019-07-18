---
title: Добавить в рабочую область узлы результат поиска набора схем XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ba709e90de580aacda2034eca319a419583dac0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783694"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Практическое руководство. Добавление в рабочую область узлов, полученных в результате поиска набора схем

В этом разделе объясняется, как добавить узлы, которые выделены в **обозреватель XML-схем** в результате поиска по ключевому слову в рабочей области.

> [!NOTE]
> Только глобальные узлы, которые могут добавляться к [рабочей области](../xml-tools/xml-schema-designer-workspace.md).

 В этом примере используется образец [схема заказа на покупку](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Добавление результирующих узлов набора схем

1. Выполните действия, описанные в [как: Создание и изменение файла схемы XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. В текстовом поле поиска введите «purchaseOrder» [обозреватель XML](../xml-tools/xml-schema-explorer.md) панель инструментов и нажмите кнопку поиска.

     ![Поиск по ключевым словам в обозревателе схемы XML](../xml-tools/media/schemaexplorersearch.gif)

     Результаты поиска выделяются цветом **обозреватель XML-схем** и отмечаются галочками на вертикальной полосе прокрутки.

3. Добавить результаты поиска в рабочую область, щелкнув **Добавить выделенные узлы в рабочую область** кнопку на панели сводных результатов.

     ![Результат поиска в обозревателе схемы XML](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder` Узла и `PurchaseOrderType` узел отображаться рядом друг с другом в области конструктора [представление графика](../xml-tools/graph-view.md). Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.