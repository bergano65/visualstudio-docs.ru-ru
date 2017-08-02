---
title: "Как добавлять в рабочую область узлы, полученные в результате поиска набора схем | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# Как добавлять в рабочую область узлы, полученные в результате поиска набора схем
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Данный раздел объясняет процесс добавления узлов, выделенных в обозревателе XML\-схем в результате поиска по ключевому слову в рабочей области.  
  
> [!NOTE]
>  В [рабочую область](../xml-tools/xml-schema-designer-workspace.md) можно добавлять только глобальные узлы.  
  
 Данный пример использует образец [Схемы заказа на покупку](../Topic/Sample%20XSD%20File:%20Purchase%20Order%20Schema.md).  
  
### Добавление результирующих узлов набора схем  
  
1.  Следуйте шагам, описанным в разделе [Как создавать и изменять файл XSD\-схемы](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  Введите "purchaseOrder" в текстовом поле поиска панели инструментов [Обозреватель XML](../xml-tools/xml-schema-explorer.md) и нажмите кнопку поиска.  
  
     ![Поиск по ключевым словам в обозревателе схемы XML](~/xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Результаты поиска также выделяются в обозревателе XML\-схем и отмечаются галочками на вертикальной полосе прокрутки.  
  
3.  Добавьте результаты поиска в рабочую область, нажав кнопку **Добавить выделенные узлы в рабочую область** на панели сводных результатов.  
  
     ![Результат поиска в обозревателе схемы XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     Узел `purchaseOrder` и узел `PurchaseOrderType` будут отображены рядом друг с другом в области конструктора в [Представлении графиков](../xml-tools/graph-view.md).Поскольку два узла связаны друг с другом \(элемент `purchaseOrder` является типом `PurchaseOrderType`\), между ними появится стрелочка.