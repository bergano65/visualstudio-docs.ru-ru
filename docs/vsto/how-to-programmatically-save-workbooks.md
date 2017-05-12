---
title: "Практическое руководство. Программное сохранение книг Excel"
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
  - "книги, сохранение"
  - "книги, сохранение резервных копий"
  - "книги, сохранение в формате XML"
ms.assetid: 991ccf9b-5213-4094-9030-284ec167bdcc
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# Практическое руководство. Программное сохранение книг Excel
  Сохранить книгу можно несколькими способами.  Можно сохранить книгу без изменения пути к файлу.  Если книга не сохранялась ранее, следует сохранить книгу, указав путь.  Без явного пути Microsoft Office Excel сохраняет файл в текущей папке с именем, заданным при его создании.  Можно также сохранить копию книги, не изменяя открытую книгу в памяти.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Сохранение книги без изменения пути  
  
#### Сохранение книги, связанной с настройкой на уровне документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> класса ThisWorkbook.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#4)]  
  
#### Сохранение активной книги в надстройке VSTO  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A>, чтобы сохранить активную книгу.  Чтобы использовать следующий пример кода, запустите его в классе `ThisAddIn` в проекте надстройки VSTO для Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## Сохранение книги с новым путем  
 Вы можете сохранить указанную книгу в новой папке или с новым именем, указав при необходимости формат файла, пароль, режим доступа и т. д.  
  
> [!NOTE]  
>  Вам может потребоваться задать свойство <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> как **False** перед сохранением книги с новым путем, так как для сохранения в некоторых форматах требуется взаимодействие с пользователем.  Если присвоить этому свойству значение **False**, Excel будет использовать все значения по умолчанию.  
  
#### Сохранение книги, связанной с настройкой на уровне документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> класса `ThisWorkbook`.  Чтобы использовать следующий пример кода, запустите его из класса `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#5)]  
  
#### Сохранение активной книги в надстройке VSTO  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A>, чтобы сохранить активную книгу с новым путем.  Чтобы использовать следующий пример кода, запустите его в классе `ThisAddIn` в проекте надстройки VSTO для Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## Сохранение копии книги  
 Вы можете также сохранить копию книги в файл, не изменяя открытую книгу в памяти.  Это полезно, если вам нужно создать резервную копию без изменения местоположения книги.  
  
#### Сохранение книги, связанной с настройкой на уровне документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> класса `ThisWorkbook`.  Чтобы использовать следующий пример кода, запустите его из класса `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#6)]  
  
#### Сохранение активной книги в надстройке VSTO  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A>, чтобы сохранить копию активной книги.  Чтобы использовать следующий пример кода, запустите его в классе `ThisAddIn` в проекте надстройки VSTO для Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#5)]  
  
## Отказоустойчивость  
 Интерактивная отмена любых методов, которые сохраняют или копируют книгу, вызывает ошибку времени выполнения в коде.  Например, если процедура вызывает метод <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A>, но он не отключает запросы Excel, и ваш пользователь нажимает кнопку **Отменить** в ответ на запрос Excel, возникает ошибка времени выполнения.  
  
## См. также  
 [Работа с книгами](../vsto/working-with-workbooks.md)   
 [Ведущий элемент книги](../vsto/workbook-host-item.md)   
 [Практическое руководство. Программное закрытие книг Excel](../vsto/how-to-programmatically-close-workbooks.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)  
  
  