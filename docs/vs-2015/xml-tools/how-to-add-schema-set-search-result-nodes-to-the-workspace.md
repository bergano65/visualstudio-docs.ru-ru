---
title: 'Способ: добавить в рабочую область узлы результат поиска набора схем | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 75f254a8f64c3750a3c89e10016a0520d3760847
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210370"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Как добавлять в рабочую область узлы, полученные в результате поиска набора схем
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Данный раздел объясняет процесс добавления узлов, выделенных в обозревателе XML-схем в результате поиска по ключевому слову в рабочей области.  
  
> [!NOTE]
>  Только глобальные узлы, которые могут добавляться к [рабочей области](../xml-tools/xml-schema-designer-workspace.md).  
  
 В этом примере используется образец [схемы заказа на покупку](../xml-tools/sample-xsd-file-purchase-order-schema.md).  
  
### <a name="to-add-schema-set-result-nodes"></a>Добавление результирующих узлов набора схем  
  
1.  Выполните действия, описанные в [как: Создание и изменение файла схемы XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  В текстовом поле поиска введите «purchaseOrder» [обозреватель XML](../xml-tools/xml-schema-explorer.md) панель инструментов и нажмите кнопку поиска.  
  
     ![Поиск по ключевому слову обозреватель схемы XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Результаты поиска также выделяются в обозревателе XML-схем и отмечаются галочками на вертикальной полосе прокрутки.  
  
3.  Добавить результаты поиска в рабочую область, щелкнув **Добавить выделенные узлы в рабочую область** кнопку на панели сводных результатов.  
  
     ![Результаты поиска в обозревателе схемы XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     `purchaseOrder` Узла и `PurchaseOrderType` узел отображаться рядом друг с другом в области конструктора [представление графика](../xml-tools/graph-view.md). Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.



