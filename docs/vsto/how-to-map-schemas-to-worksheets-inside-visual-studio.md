---
title: "Практическое руководство. Сопоставление схем и листов внутри Visual Studio"
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
  - "Excel [разработка решений Office в Visual Studio], схемы XML"
  - "сопоставления [разработка решений Office в Visual Studio], схем XML листам Excel"
  - "листы [разработка решений Office в Visual Studio], схемы XML"
  - "схемы XML [разработка решений Office в Visual Studio], сопоставление"
ms.assetid: cef3f751-c1cf-46f3-9177-0bacdcee4121
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Практическое руководство. Сопоставление схем и листов внутри Visual Studio
  Схему XML можно сопоставить с листом, когда лист открыт в Visual Studio.  Для этого используются те же средства Microsoft Office Excel, что и при открытии листа вне Visual Studio.  Проект Office создает те же самые объекты вне зависимости от того, происходит ли сопоставление с листом до или после создания решения Excel.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Нельзя использовать составные XML\-схемы в решениях Excel.  
  
### Сопоставление схемы XML и листа Excel в Visual Studio  
  
1.  Откройте книгу Excel или шаблонный проект в Visual Studio.  
  
2.  Щелкните рабочий лист для перемещения фокуса конструктора.  
  
3.  В ленте щелкните вкладку **Разработчик**.  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается в ленте, то ее следует сначала отобразить.  Дополнительные сведения см. в разделе [Практическое руководство. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  В группе **XML** щелкните элемент **Источник**.  
  
     Откроется окно **XML\-источник**.  
  
5.  В окне **XML\-источник** щелкните **Карты XML**.  
  
     Откроется диалоговое окно **Карты XML**.  
  
6.  В диалоговом окне **Карты XML** нажмите кнопку **Добавить**.  
  
7.  Найдите файл схемы, выберите его и нажмите **Открыть**.  
  
8.  Нажмите кнопку **ОК**.  
  
     Схема отобразится в окне **XML\-источник**.  В проекте создается типизированный <xref:System.Data.DataSet> на основе схемы, а также <xref:System.Windows.Forms.BindingSource>.  
  
9. Перетащите элементы из окна **XML\-источник** в те места листа, где необходимо создать соответствующие элементы управления.  
  
     При перетаскивании не повторяющиеся элемент схемы проекта office создает элемент управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, которое автоматически привязано к <xref:System.Windows.Forms.BindingSource>.  
  
     При перетаскивании повторяющегося элемента схемы проекта office создает элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject>, автоматически не привязано к источнику данных.  Дополнительные сведения см. в разделе [XML-схемы и данные в настройках на уровне документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md).  
  
## См. также  
 [Практическое руководство. Сопоставление схем и документов Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [XML-схемы и данные в настройках на уровне документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  