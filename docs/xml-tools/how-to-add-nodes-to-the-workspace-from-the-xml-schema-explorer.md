---
title: "Как: добавлять узлы в рабочую область из обозревателя XML-схем | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 37da28d4c5db1e008af29c03997943720dcfbada
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Как добавлять узлы в рабочую область в обозревателе XML-схем
В этом разделе объясняется, как добавить узлы в [рабочей области конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md) из обозревателя XML-схем. Цель может быть достигнута посредством перетаскивания узлов из обозревателя XML-схемы на представление конструктора XSD, или использованием контекстного меню обозревателя XML-схем. Можно также добавить узлы, выделенные в результате поиска, выполненного в обозревателе XML-схем. Дополнительные сведения см. в разделе [как: Добавление схемы задать поиска результат узлов в рабочую область](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).  
  
> [!NOTE]
>  Можно добавлять только глобальные узлы для [рабочей области конструктора схем XML](../xml-tools/xml-schema-designer-workspace.md).  
  
### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Добавление узла посредством контекстного меню обозревателя XML  
  
1.  Следуйте указаниям в [как: Создание и изменение файла XSD-схемы](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  В обозревателе XSD щелкните правой кнопкой мыши узел `PurchaseOrderType`. Выберите **Показать в представлении графика**.  
  
     Узел `purchaseOrderType` будет отображен в области конструктора в представлении графиков.  
  
### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Перетаскивание узла на представление  
  
1.  В представлении графика щелкните правой кнопкой мыши узел `PurchaseOrderType`. Выберите **Показать в обозревателе XML-схем**.  
  
     Узел будет выделен в обозревателе XML-схем.  
  
2.  Щелкните правой кнопкой мыши `PurchaseOrderType` в обозревателе XML-схем и выбрать **Показать все ссылки**.  
  
     Узел `purchaseOrder` выделен.  
  
3.  Перетащите узел `purchaseOrder` в представление графика.  
  
     Узел `purchaseOrder` и узел `PurchaseOrderType` будут отображены рядом друг с другом в области конструктора в представлении графиков. Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.  
  
### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Добавление узлов с использованием возможностей поиска обозревателя схем  
  
1.  В текстовом поле поиска введите «purchaseOrder» [обозреватель XML](../xml-tools/xml-schema-explorer.md) панель инструментов и нажмите кнопку поиска.  
  
     ![Поиск по ключевому слову обозреватель схемы XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Результаты поиска также выделяются в обозревателе XML-схем и отмечаются галочками на вертикальной полосе прокрутки.  
  
2.  Добавить результаты поиска в рабочую область, щелкнув **Добавить выделенные узлы в рабочую область** кнопку на панели сводных результатов.  
  
     ![Результаты поиска в обозревателе схемы XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     `purchaseOrder` Узла и `PurchaseOrderType` узла отображаются рядом друг с другом в области конструктора на [представление графика](../xml-tools/graph-view.md). Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.  
  
## <a name="see-also"></a>См. также  
 [Обозреватель схемы XML](../xml-tools/xml-schema-explorer.md)