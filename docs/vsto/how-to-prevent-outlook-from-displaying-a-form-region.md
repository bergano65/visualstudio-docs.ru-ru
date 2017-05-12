---
title: "Практическое руководство. Отсутствие отображения области формы в Outlook"
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
  - "отмена из области отображения"
  - "области формы [разработка решений Office в Visual Studio], отмена отображения"
ms.assetid: 82a25def-776a-476a-a72d-d0a48a827d3c
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Практическое руководство. Отсутствие отображения области формы в Outlook
  Возможны ситуации, когда в Microsoft Office Outlook отображение области формы для конкретного элемента может быть нежелательным.  Например, если элемент контакта не содержит рабочий адрес, можно запретить отображение местонахождения предприятия в схеме.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### Блокирование отображения области формы в Outlook  
  
1.  Откройте файл с кодом той области формы, которую требуется изменить.  
  
2.  Разверните область кода **Производство областей формы**.  
  
3.  Добавьте код `FormRegionInitializing` в обработчике событий, который задает для свойства <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> класса <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> значение **true**.  
  
 В приведенном примере элемент контактов не содержит адресов, поэтому <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> свойство устанавливается в **true** и область формы не отображается.  
  
## Пример  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#1)]  
  
## См. также  
 [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)   
 [Пошаговое руководство. Разработка области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Практическое руководство. Добавление области формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Пошаговое руководство. Разработка области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Пошаговое руководство. Импорт области формы, созданной в Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  