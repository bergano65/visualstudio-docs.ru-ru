---
title: Как добавить узлы результатов поиска набора схем в рабочую область | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b34be331ad3ec67e2c3bd8d9ecc500cd256b1b09
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666550"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Как добавлять в рабочую область узлы, полученные в результате поиска набора схем
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Данный раздел объясняет процесс добавления узлов, выделенных в обозревателе XML-схем в результате поиска по ключевому слову в рабочей области.

> [!NOTE]
> В [рабочую область](../xml-tools/xml-schema-designer-workspace.md)можно добавлять только глобальные узлы.

 В этом примере используется [схема образца заказа на покупку](../xml-tools/sample-xsd-file-purchase-order-schema.md).

### <a name="to-add-schema-set-result-nodes"></a>Добавление результирующих узлов набора схем

1. Выполните действия, описанные в разделе [Создание и изменение файла XSD-схемы](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Введите "purchaseOrder" в текстовом поле "Поиск" на панели инструментов [проводника XML](../xml-tools/xml-schema-explorer.md) и нажмите кнопку "Поиск".

     ![Поиск ключевых слов обозревателя XML-схем](../xml-tools/media/schemaexplorersearch.gif "счемаексплорерсеарч")

     Результаты поиска также выделяются в обозревателе XML-схем и отмечаются галочками на вертикальной полосе прокрутки.

3. Добавьте результаты поиска в рабочую область, нажав кнопку **Добавить выделенные узлы в рабочую область** на панели сводки результатов.

     ![Результаты поиска в обозревателе XML-схем](../xml-tools/media/schemaexplorersearchresult.gif "счемаексплорерсеарчресулт")

     Узел `purchaseOrder` и узел `PurchaseOrderType` отображаются рядом друг с другом в области конструктора [представления графа](../xml-tools/graph-view.md). Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.
