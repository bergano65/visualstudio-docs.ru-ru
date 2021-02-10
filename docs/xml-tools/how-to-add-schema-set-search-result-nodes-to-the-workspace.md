---
title: Добавление узлов, полученных в результате поиска набора схем
description: Узнайте, как добавлять узлы, выделенные в обозревателе XML-схем в результате поиска по ключевому слову в рабочей области.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 762992ab2649e59055af8fd656514f3e82e9e8de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879219"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Практическое руководство. Добавление в рабочую область узлов, полученных в результате поиска набора схем

В данном разделе объясняется процесс добавления узлов, выделенных в **обозревателе схемы XML** в результате поиска по ключевому слову в рабочей области.

> [!NOTE]
> В [рабочую область](../xml-tools/xml-schema-designer-workspace.md) можно добавлять только глобальные узлы.

В этом примере используется образец [схемы заказа на покупку](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Добавление результирующих узлов набора схем

1. Выполните действия, описанные в статье [Практическое руководство. Создание и изменение файла схемы XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Введите purchaseOrder в текстовом поле поиска панели инструментов [обозревателя схемы XML](../xml-tools/xml-schema-explorer.md) и нажмите кнопку поиска.

     ![Поиск по ключевым словам в обозревателе схемы XML](../xml-tools/media/schemaexplorersearch.gif)

     Результаты поиска также выделяются в **обозревателе схемы XML** и отмечаются галочками на вертикальной полосе прокрутки.

3. Добавьте результаты поиска в рабочую область, нажав кнопку **Добавить выделенные узлы в рабочую область** на панели сводных результатов.

     ![Результат поиска в обозревателе схемы XML](../xml-tools/media/schemaexplorersearchresult.gif)

     Узлы `purchaseOrder` и `PurchaseOrderType` будут отображены рядом друг с другом в области конструктора в [представлении графика](../xml-tools/graph-view.md). Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.
