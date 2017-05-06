---
title: "Практическое руководство. Программная защита книг Excel"
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
  - "защита документов, добавление в книги Excel"
  - "защита документов, удаление из книг"
  - "документы [разработка решений Office в Visual Studio], защита документов"
  - "книги, пароли"
  - "книги, защита"
  - "книги, снятие защиты"
ms.assetid: 553c67b9-e2a4-46b6-878c-5b4b4efa4589
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Практическое руководство. Программная защита книг Excel
  Существует возможность программными средствами защитить рабочую книгу Microsoft Office Excel так, что пользователи не смогут добавлять или удалять рабочие листы, а также снять защиту с книги.  Кроме того, можно дополнительно установить пароль, указать необходимость защиты структуры \(чтобы пользователи не могли перемещать листы\) и необходимость защиты окон рабочей книги.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 При применении защиты к рабочей книге пользователям не запрещается редактировать ячейки.  Для защиты данных необходимо применить защиту к рабочим листам.  Дополнительные сведения см. в разделе [Практическое руководство. Программная защита листов Excel](../vsto/how-to-programmatically-protect-worksheets.md).  
  
 В следующих примерах кода используется переменная, которая содержит пароль, полученный от пользователя.  
  
## Защита книги, являющейся частью настройки уровня документа  
  
#### Защита рабочей книги  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> рабочей книги и включите пароль:  Чтобы использовать следующий пример кода, запустите его из класса `ThisWorkbook`, а не из класса листа.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#10)]  
  
#### Снятие защиты с рабочей книги  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A>, передав ему при необходимости пароль:  Чтобы использовать следующий пример кода, запустите его из класса `ThisWorkbook`, а не из класса листа.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#11)]  
  
## Защита книги при помощи надстройки уровня приложения  
  
#### Защита рабочей книги  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> рабочей книги и включите пароль:  Этот пример кода использует активную книгу.  Чтобы воспользоваться этим примером, запустите его из класса `ThisAddIn` своего проекта.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#6)]  
  
#### Снятие защиты с рабочей книги  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> активной книги, передав ему при необходимости пароль:  Чтобы воспользоваться этим примером, запустите его из класса `ThisAddIn` своего проекта.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#7)]  
  
## См. также  
 [Работа с книгами](../vsto/working-with-workbooks.md)   
 [Практическое руководство. Программная защита листов Excel](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Практическое руководство. Программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  