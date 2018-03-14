---
title: "Как: сопоставление схем и листов внутри Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: ed0da1c2ac181db93105a93dd2269be55f0379a2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Практическое руководство. Сопоставление схем и листов внутри Visual Studio
  XML-схемы можно сопоставить с листа, когда лист открыт в Visual Studio. Можно использовать те же средства Microsoft Office Excel, которые используются, если книга открыта вне Visual Studio. Проект Office создает те же объекты, будет ли сопоставления схемы с листом до или после создания решения Excel.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Нельзя использовать составные XML-схемы в решениях Excel.  
  
### <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Для сопоставления XML-схемы в лист Excel в Visual Studio  
  
1.  Откройте проект книги или шаблон Excel в Visual Studio.  
  
2.  Выберите лист для перемещения фокуса в конструктор.  
  
3.  На ленте перейдите на вкладку **Разработчик** .  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [Практическое руководство. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  В **XML** щелкните **источника**.  
  
     **XML-источник** открывается окно.  
  
5.  В **XML-источник** окно, нажмите кнопку **карты XML**.  
  
     **Карты XML** откроется диалоговое окно.  
  
6.  В **карты XML** диалоговое окно, нажмите кнопку **добавить**.  
  
7.  Перейдите к нужному файлу схемы, выберите его и нажмите кнопку **откройте**.  
  
8.  Нажмите кнопку **ОК**.  
  
     Схема отобразится в **XML-источник** окна. В проекте типизированный <xref:System.Data.DataSet> создается на основе схемы и <xref:System.Windows.Forms.BindingSource> создается.  
  
9. Перетащите элементы из **XML-источник** окна на части листа, где необходимо создать соответствующие элементы управления.  
  
     При перетаскивании неповторяющегося элемента схемы проекта Office приводит к возникновению ошибки <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> управления, автоматически привязывается к <xref:System.Windows.Forms.BindingSource>.  
  
     При перетаскивании повторяющегося элемента схемы проекта Office приводит к возникновению ошибки <xref:Microsoft.Office.Tools.Excel.ListObject> элемента управления, который автоматически не привязан к источнику данных. Дополнительные сведения см. в разделе [XML-схемы и данные в настройках уровня документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md).  
  
## <a name="see-also"></a>См. также  
 [Как: сопоставление схем в документы Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [XML-схемы и данные в настройках на уровне документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  