---
title: Практическое руководство. Добавление узлов в рабочую область в обозревателе схем XML | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 84a99426cf32477e0661872c09f41ec50aeb2842
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978553"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Практическое руководство. Добавление узлов в рабочую область в обозревателе схем XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
В этом разделе объясняется, как добавить узлы в [рабочей области конструктора XML-схем](../xml-tools/xml-schema-designer-workspace.md) обозревателе XML-схем. Цель может быть достигнута посредством перетаскивания узлов из обозревателя XML-схемы на представление конструктора XSD, или использованием контекстного меню обозревателя XML-схем. Можно также добавить узлы, выделенные в результате поиска, выполненного в обозревателе XML-схем. Дополнительные сведения см. в разделе [Как Добавить в рабочую область узлы результат поиска набора схем](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).  
  
> [!NOTE]
>  Только глобальные узлы, которые могут добавляться к [рабочей области конструктора схем XML](../xml-tools/xml-schema-designer-workspace.md).  
  
### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Добавление узла посредством контекстного меню обозревателя XML  
  
1.  Выполните действия, описанные в [как: Создание и изменение файла схемы XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  В обозревателе XSD щелкните правой кнопкой мыши узел `PurchaseOrderType`. Выберите **Показать в представлении графика**.  
  
     Узел `purchaseOrderType` будет отображен в области конструктора в представлении графиков.  
  
### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Перетаскивание узла на представление  
  
1.  В представлении графика щелкните правой кнопкой мыши узел `PurchaseOrderType`. Выберите **Показать в обозревателе XML-схем**.  
  
     Узел будет выделен в обозревателе XML-схем.  
  
2.  Щелкните правой кнопкой мыши `PurchaseOrderType` узел в обозревателе XML-схем и выберите **Показать все ссылки**.  
  
     Узел `purchaseOrder` выделен.  
  
3.  Перетащите узел `purchaseOrder` в представление графика.  
  
     Узел `purchaseOrder` и узел `PurchaseOrderType` будут отображены рядом друг с другом в области конструктора в представлении графиков. Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.  
  
### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Добавление узлов с использованием возможностей поиска обозревателя схем  
  
1.  В текстовом поле поиска введите «purchaseOrder» [обозреватель XML](../xml-tools/xml-schema-explorer.md) панель инструментов и нажмите кнопку поиска.  
  
     ![Поиск по ключевому слову обозреватель схемы XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Результаты поиска также выделяются в обозревателе XML-схем и отмечаются галочками на вертикальной полосе прокрутки.  
  
2.  Добавить результаты поиска в рабочую область, щелкнув **Добавить выделенные узлы в рабочую область** кнопку на панели сводных результатов.  
  
     ![Результаты поиска в обозревателе схемы XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     `purchaseOrder` Узла и `PurchaseOrderType` узел отображаться рядом друг с другом в области конструктора [представление графика](../xml-tools/graph-view.md). Поскольку два узла связаны друг с другом (элемент `purchaseOrder` является типом `PurchaseOrderType`), между ними появится стрелочка.  
  
## <a name="see-also"></a>См. также  
 [Обозреватель схемы XML](../xml-tools/xml-schema-explorer.md)
