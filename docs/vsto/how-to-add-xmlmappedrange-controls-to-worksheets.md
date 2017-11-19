---
title: "Как: Добавление элементов управления XMLMappedRange на листы | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: e1d4f2a8-1157-49c2-9158-a1253b709cb8
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d83241e265db0e0ef0165cbc1615f23ea2ec5a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Практическое руководство. Добавление элементов управления XMLMappedRange на листы
  При сопоставлении XML-элемент с ячейкой в Microsoft Office Excel, Visual Studio автоматически добавляет <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> лист элемента управления.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Управления не доступен на **элементов** или **источники данных** окна. Кроме того, не удается создать <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> элементы управления программными средствами.  
  
### <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Чтобы добавить элемент управления XMLMappedRange на лист  
  
1.  Откройте книгу Excel в конструкторе Visual Studio.  
  
2.  Откройте таблицу, в которой вы хотите добавить элемент управления.  
  
3.  На **разработчика** щелкните **источника**.  
  
    > [!NOTE]  
    >  Если **разработчика** вкладка не отображается на ленте, необходимо включить его. Дополнительные сведения см. в разделе [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
     **XML-источник** отображается область задач.  
  
4.  В **XML-источник** области задач, нажмите кнопку **карты XML**.  
  
5.  В **карты XML** диалоговое окно, нажмите кнопку **добавить**.  
  
     **XML-источник** откроется диалоговое окно.  
  
6.  Выберите XML-схемы из **XML-источник** диалоговое окно и нажмите кнопку **откройте**.  
  
     Схема добавляется к **карты XML** диалоговое окно.  
  
7.  В **карты XML** диалоговое окно, нажмите кнопку **ОК**.  
  
8.  Перетащите элемент из **XML-источник** области задач в ячейку на листе.  
  
     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Создается и добавляется в проект.  
  
    > [!NOTE]  
    >  При перетаскивании родительского элемента из **XML-источник** область задач <xref:Microsoft.Office.Tools.Excel.ListObject> создается элемент управления.  
  
## <a name="see-also"></a>См. также  
 [Элемент управления XmlMappedRange](../vsto/xmlmappedrange-control.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Практическое руководство. Сопоставление схем и листов в Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  