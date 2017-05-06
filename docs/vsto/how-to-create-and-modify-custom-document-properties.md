---
title: "Практическое руководство. Создание и изменение настраиваемых свойств документа"
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
  - "настраиваемые свойства документа"
  - "документы [разработка решений Office в Visual Studio], свойства"
  - "свойства документов [разработка решений Office в Visual Studio]"
ms.assetid: 99d9dfaf-891f-4f3b-a580-67362afdaf34
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Практическое руководство. Создание и изменение настраиваемых свойств документа
  Перечисленные выше приложения Microsoft Office предоставляют встроенные свойства, которые хранятся в документах. Кроме того, можно создавать и изменять настраиваемые свойства документа при наличии дополнительных сведений, которые необходимо хранить вместе с документом.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Используйте свойство CustomDocumentProperties документа для работы с пользовательскими свойствами. Например, в проекте уровня документа для Microsoft Office Excel используйте свойство <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> класса `ThisWorkbook`. В проекте надстройки VSTO для Excel используйте свойство <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> объекта <xref:Microsoft.Office.Interop.Excel.Workbook>. Эти свойства возвращают объект <xref:Microsoft.Office.Core.DocumentProperties>, который представляет собой коллекцию объектов <xref:Microsoft.Office.Core.DocumentProperty>. Для извлечения конкретного свойства по имени или по индексу в коллекции можно использовать свойство `Item` коллекции.  
  
 В следующем примере показано, как добавить пользовательское свойство в настройку уровня документа для Excel и присвоить ему значение.  
  
 ![ссылка на видео](../vsto/media/playvideo.png "ссылка на видео") Демонстрационные видеоматериалы см. на странице [Раздел справки: доступ к настраиваемым свойствам документов в Microsoft Word и работа с ними](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## Пример  
 [!code-csharp[Trin_VstcoreProgramming#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#6)]
 [!code-vb[Trin_VstcoreProgramming#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#6)]  
  
## Отказоустойчивость  
 При попытке доступа к свойству `Value` для неопределенного свойства возникает исключение.  
  
## См. также  
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Настройки программирования уровня документа](../vsto/programming-document-level-customizations.md)   
 [Практическое руководство. Чтение и запись в свойства документа](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  