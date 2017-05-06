---
title: "Практическое руководство. Добавление элементов управления XMLMappedRange на листы"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "элементы управления [разработка решений Office в Visual Studio], добавление к листам"
  - "XMLMappedRange - элемент управления, добавление к листам"
ms.assetid: e1d4f2a8-1157-49c2-9158-a1253b709cb8
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Практическое руководство. Добавление элементов управления XMLMappedRange на листы
  При сопоставлении XML\-элемента с ячейкой в Microsoft Office Excel Visual Studio автоматически добавляет в лист элемент управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Элемент управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> недоступен в окне **Панель элементов** или **Источники данных**.  Кроме того, элементы управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> можно создать программным путем.  
  
### Добавление элемента управления XMLMappedRange на лист  
  
1.  Откройте книгу Excel в конструкторе Visual Studio.  
  
2.  Откройте лист, на который требуется добавить элемент управления.  
  
3.  На вкладке **Разработчик** щелкните элемент **Исходный код**.  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается в ленте, то ее следует включить.  Дополнительные сведения см. в разделе [Практическое руководство. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
     Отобразится область задач **XML\-источник**:  
  
4.  В области задач **XML\-источник** щелкните **Карты XML**.  
  
5.  В диалоговом окне **Карты XML** нажмите кнопку **Добавить**.  
  
     Откроется диалоговое окно **XML\-источник**.  
  
6.  В диалоговом окне **XML\-источник** выберите XML\-схему и щелкните элемент **Открыть**.  
  
     Схема добавится в диалоговое окно **Карты XML**.  
  
7.  В диалоговом окне **Карты XML** нажмите кнопку **ОК**.  
  
8.  Перетащите элемент из области задач **XML\-источник** на ячейку листа.  
  
     Элемент управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> будет создан и добавлен в проект.  
  
    > [!NOTE]  
    >  При перетаскивании родительского элемента из области задач **XML\-источник** создается элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
## См. также  
 [Элемент управления XmlMappedRange](../vsto/xmlmappedrange-control.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Практическое руководство. Сопоставление схем и листов внутри Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  