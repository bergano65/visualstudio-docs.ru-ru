---
title: Добавление узлов в рабочую область из обозревателя XML-схемы
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2049b8da1caa4e0af0afc52aec6e75f499d85b8b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592819"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Как добавить узлы в рабочую область из обозревателя XML-схем

В этом разделе описывается добавление узлов в [рабочую область конструктора схем XML](../xml-tools/xml-schema-designer-workspace.md) из **обозревателя XML-схем**. Это можно сделать, перетащив узлы из **обозревателя XML-схем** в представление конструктора XSD или используя контекстное меню **обозревателя схемы XML** . Можно также добавить узлы, выделенные в результате поиска, выполняемого **обозревателем XML-схем**. Дополнительные сведения см. в разделе [как добавить в рабочую область узлы результатов поиска набора схем](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> В [рабочую область конструктора схем XML](../xml-tools/xml-schema-designer-workspace.md)можно добавлять только глобальные узлы.

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Добавление узлов с помощью контекстного меню проводника XML

1. Выполните действия, описанные в разделе [Создание и изменение файла XSD-схемы](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Щелкните правой кнопкой мыши узел `PurchaseOrderType` в обозревателе XSD. Выберите **Показать в представлении графика**.

     Узел `purchaseOrderType` будет отображен в области конструктора в представлении графиков.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Перетаскивание узла на представление

1. Щелкните правой кнопкой мыши узел `PurchaseOrderType` в представлении графа. Выберите команду " **отобразить" в обозревателе XML-схем**.

     Узел выделяется в **обозревателе XML-схем**.

2. Щелкните правой кнопкой мыши узел `PurchaseOrderType` в **обозревателе XML-схем** и выберите пункт **отобразить все ссылки**.

     Узел `purchaseOrder` выделен.

3. Перетащите узел `purchaseOrder` в представление графика.

     Узел `purchaseOrder` и узел `PurchaseOrderType` будут отображены рядом друг с другом в области конструктора в представлении графиков. Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Добавление узлов с использованием возможностей поиска обозревателя схем

1. Введите "purchaseOrder" в текстовом поле "Поиск" на панели инструментов [проводника XML](../xml-tools/xml-schema-explorer.md) и нажмите кнопку "Поиск".

     ![Поиск по ключевому слову в обозревателе схемы XML](../xml-tools/media/schemaexplorersearch.gif)

     Результаты поиска выделяются в **обозревателе XML-схем** и помечаются делениями на вертикальной полосе прокрутки.

2. Добавьте результаты поиска в рабочую область, нажав кнопку **Добавить выделенные узлы в рабочую область** на панели сводки результатов.

     ![Результаты поиска в обозревателе схемы XML](../xml-tools/media/schemaexplorersearchresult.gif)

     Узел `purchaseOrder` и узел `PurchaseOrderType` отображаются рядом друг с другом в области конструктора [представления графа](../xml-tools/graph-view.md). Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.

## <a name="see-also"></a>См. также:

- [Обозреватель схемы XML](../xml-tools/xml-schema-explorer.md)
