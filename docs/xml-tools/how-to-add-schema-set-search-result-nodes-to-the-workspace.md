---
title: Добавление узлов результатов поиска из набора XML-схем в рабочую область
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1bdb21c2b9ce3f6a79bf24738c84fcb3064c24cb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592793"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Как добавить узлы результатов поиска набора схем в рабочую область

В этом разделе объясняется, как добавить узлы, выделенные в **обозревателе XML-схем** , в результате поиска ключевых слов в рабочей области.

> [!NOTE]
> В [рабочую область](../xml-tools/xml-schema-designer-workspace.md)можно добавлять только глобальные узлы.

В этом примере используется [схема образца заказа на покупку](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Добавление результирующих узлов набора схем

1. Выполните действия, описанные в разделе [Создание и изменение файла XSD-схемы](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Введите "purchaseOrder" в текстовом поле "Поиск" на панели инструментов [проводника XML](../xml-tools/xml-schema-explorer.md) и нажмите кнопку "Поиск".

     ![Поиск по ключевому слову в обозревателе схемы XML](../xml-tools/media/schemaexplorersearch.gif)

     Результаты поиска выделяются в **обозревателе XML-схем** и помечаются делениями на вертикальной полосе прокрутки.

3. Добавьте результаты поиска в рабочую область, нажав кнопку **Добавить выделенные узлы в рабочую область** на панели сводки результатов.

     ![Результаты поиска в обозревателе схемы XML](../xml-tools/media/schemaexplorersearchresult.gif)

     Узел `purchaseOrder` и узел `PurchaseOrderType` отображаются рядом друг с другом в области конструктора [представления графа](../xml-tools/graph-view.md). Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.
