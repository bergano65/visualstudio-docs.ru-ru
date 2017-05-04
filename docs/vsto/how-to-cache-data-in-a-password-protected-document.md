---
title: "Практическое руководство. Кэширование данных в документе, защищенном паролем | Microsoft Docs"
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
  - "данные [разработка решений Office в Visual Studio], кэширование"
  - "кэширование данных [разработка решений Office в Visual Studio], защищенные документы"
  - "наборы данных [разработка решений Office в Visual Studio], кэширование"
ms.assetid: 91b865fc-bd01-438f-ac63-2fe3175bc2e8
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Практическое руководство. Кэширование данных в документе, защищенном паролем
  Если добавить данные в кэш данных в документе или книге, защищенной паролем, изменения, вносимые в кэшированные данные, не сохраняются автоматически.  Можно сохранить изменения в кэшированные данные путем переопределения двух методов в проекте.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Кэширование в документах Word  
  
#### Кэширование данных в документах Word, защищенных паролем  
  
1.  В классе `ThisDocument` пометьте открытое поле или свойство, которое будет кэшироваться.  Дополнительные сведения см. в разделе [Кэширование данных](../vsto/caching-data.md).  
  
2.  Переопределите метод <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> в классе `ThisDocument` и удалите защиту из документа.  
  
     При сохранении документа среда времени [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность снять защиту с документа.  Это позволяет сохранить изменения кэшированных данных.  
  
3.  Переопределите метод <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> в классе `ThisDocument` и восстановите защиту документа.  
  
     После сохранении документа среда [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность восстановить защиту документа.  
  
### Пример  
 В следующем примере кода показывается, как кэшировать данные в документе Word, защищенном паролем.  Прежде чем код удалит защиту в методе <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> он сохраняет текущее значение <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A>, позволяя повторно применить этот тип значения в методе <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>.  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/VB/ThisDocument.vb#1)]  
  
### Компиляция кода  
 Добавьте этот код, добавьте код в класс `ThisDocument` создаваемого проекта.  В этом коде предполагается, что пароль хранится в поле с именем `securelyStoredPassword`.  
  
## Кэширование в книгах Excel  
 В проектах Excel эта процедура необходима, только когда разработчик защищает всю книгу паролем с помощью метода <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A>.  Эта процедура не нужна, если разработчик защищает только конкретный лист с помощью метода <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A>.  
  
#### Кэширование данных в листе Excel, защищенном паролем  
  
1.  В классе `ThisWorkbook` или одном из классов `Sheet`*n* пометьте открытое поле или свойство, которое будет кэшироваться.  Дополнительные сведения см. в разделе [Кэширование данных](../vsto/caching-data.md).  
  
2.  Переопределите метод <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> в классе `ThisWorkbook` и удалите защиту книги.  
  
     При сохранении книги среда [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность снять защиту книги.  Это позволяет сохранить изменения кэшированных данных.  
  
3.  Переопределите метод <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> в классе `ThisWorkbook` и восстановите защиту документа.  
  
     После сохранении книги среда [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает этот метод, чтобы предоставить возможность восстановить защиту книги.  
  
### Пример  
 В следующем примере кода показывается, как кэшировать данные в книге Excel, защищенной паролем.  Прежде чем код удалит защиту в методе <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> он сохраняет текущие значения <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> и <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A>, позволяя повторно применить этот тип значения в методе <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>.  
  
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/VB/ThisWorkbook.vb#1)]  
  
### Компиляция кода  
 Добавьте этот код, добавьте код в класс `ThisWorkbook` создаваемого проекта.  В этом коде предполагается, что пароль хранится в поле с именем `securelyStoredPassword`.  
  
## См. также  
 [Кэширование данных](../vsto/caching-data.md)   
 [Практическое руководство. Кэширование данных для автономного использования или для использования на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Практическое руководство. Программное кэширование источника данных в документе MS Office.](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  