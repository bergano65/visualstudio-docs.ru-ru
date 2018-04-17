---
title: 'Как: кэширование данных в документе, защищенном паролем | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 71ce65cd253ea6473a07a98542449a1e47ae9d7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Практическое руководство. Кэширование данных в документе, защищенном паролем
  При добавлении данных в кэш данных в документе или книге, защищенной паролем, изменения кэшированных данных не сохраняются автоматически. Можно сохранить изменения в кэшированных данных путем переопределения двух методов в проекте.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="caching-in-word-documents"></a>Кэширование в документах Word  
  
#### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Кэширование данных в документе Word, защищенном паролем  
  
1.  В `ThisDocument` класса, пометьте открытое поле или свойство, которое будет кэшироваться. Для получения дополнительной информации см. [Caching Data](../vsto/caching-data.md).  
  
2.  Переопределить <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> метод `ThisDocument` класса и снять защиту с документа.  
  
     При сохранении документа [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность снять защиту документа. Это позволяет изменения кэшированных данных для сохранения.  
  
3.  Переопределить <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> метод `ThisDocument` класса и повторно применить защиту к документу.  
  
     После сохранения документа [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность восстановить защиту документа.  
  
### <a name="example"></a>Пример  
 В следующем примере кода показано, как кэшировать данные в документе Word, защищенном паролем. Прежде чем код удалит защиту в <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> метод, он сохраняет текущие <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> значение, чтобы повторно применить тот же тип защиты в <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> метод.  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]  
  
### <a name="compiling-the-code"></a>Компиляция кода  
 Добавьте следующий код в `ThisDocument` класса в проекте. В этом коде предполагается, что пароль хранится в поле с именем `securelyStoredPassword`.  
  
## <a name="caching-in-excel-workbooks"></a>Кэширование в книгах Excel  
 В проектах Excel, эта процедура необходима только в том случае, если вы защищаете всей книги с помощью пароля с помощью <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> метод. Эта процедура не требуется, если включить защиту только конкретный лист с помощью пароля с помощью <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> метод.  
  
#### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Кэширование данных в книге Excel, защищенной паролем  
  
1.  В `ThisWorkbook` класс или один из `Sheet` *n* классов, пометьте открытое поле или свойство, которое будет кэшироваться. Для получения дополнительной информации см. [Caching Data](../vsto/caching-data.md).  
  
2.  Переопределить <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> метод `ThisWorkbook` класса и снять защиту с книги.  
  
     При сохранении книги [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность снять защиту с книги. Это позволяет изменения кэшированных данных для сохранения.  
  
3.  Переопределить <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> метод `ThisWorkbook` класса и повторно применить защиту к документу.  
  
     После сохранения книги [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность восстановить защиту книги.  
  
### <a name="example"></a>Пример  
 В следующем примере кода показано, как кэшировать данные в книге Excel, защищенном паролем. Прежде чем код удалит защиту в <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> метод, он сохраняет текущие <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> и <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> значения, чтобы повторно применить тот же тип защиты в <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> метод.  
  
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]  
  
### <a name="compiling-the-code"></a>Компиляция кода  
 Добавьте следующий код в `ThisWorkbook` класса в проекте. В этом коде предполагается, что пароль хранится в поле с именем `securelyStoredPassword`.  
  
## <a name="see-also"></a>См. также  
 [Кэширование данных](../vsto/caching-data.md)   
 [Как: кэширование данных для использования в автономном режиме или на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Практическое руководство. Программное кэширование источника данных в документе Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  