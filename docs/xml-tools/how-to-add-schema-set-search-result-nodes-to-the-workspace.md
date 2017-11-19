---
title: "Способ: добавить узлы результат поиска набора схем в рабочую область | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 659eaa454243dac8ac05a5f2749237944833da10
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Как добавлять в рабочую область узлы, полученные в результате поиска набора схем
Данный раздел объясняет процесс добавления узлов, выделенных в обозревателе XML-схем в результате поиска по ключевому слову в рабочей области.  
  
> [!NOTE]
>  Можно добавлять только глобальные узлы для [рабочей](../xml-tools/xml-schema-designer-workspace.md).  
  
 В этом примере используется образец [схемы заказа на покупку](../xml-tools/sample-xsd-file-purchase-order-schema.md).  
  
### <a name="to-add-schema-set-result-nodes"></a>Добавление результирующих узлов набора схем  
  
1.  Следуйте указаниям в [как: Создание и изменение файла XSD-схемы](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  В текстовом поле поиска введите «purchaseOrder» [обозреватель XML](../xml-tools/xml-schema-explorer.md) панель инструментов и нажмите кнопку поиска.  
  
     ![Поиск по ключевому слову обозреватель схемы XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Результаты поиска также выделяются в обозревателе XML-схем и отмечаются галочками на вертикальной полосе прокрутки.  
  
3.  Добавить результаты поиска в рабочую область, щелкнув **Добавить выделенные узлы в рабочую область** кнопку на панели сводных результатов.  
  
     ![Результаты поиска в обозревателе схемы XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     `purchaseOrder` Узла и `PurchaseOrderType` узла отображаются рядом друг с другом в области конструктора на [представление графика](../xml-tools/graph-view.md). Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.