---
title: "Практическое руководство. Чтение и запись в свойства документа | Microsoft Docs"
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
  - "Word [разработка решений Office в Visual Studio], свойства документов"
  - "документы [разработка решений Office в Visual Studio], свойства"
  - "свойства документов [разработка решений Office в Visual Studio]"
  - "Excel [разработка решений Office в Visual Studio], свойства документов"
ms.assetid: e9ef9fa3-36b9-48fb-8148-f5152463c03c
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Практическое руководство. Чтение и запись в свойства документа
  Свойства документа можно сохранять вместе с документом. Приложения Office содержат различные встроенные свойства, например автора, название и тему. В этом разделе показано, как задать свойства документа в Microsoft Office Excel и Microsoft Office Word.  
  
 ![ссылка на видео](../vsto/media/playvideo.png "ссылка на видео") Демонстрационные видеоматериалы см. на странице [Раздел справки: доступ к настраиваемым свойствам документов в Microsoft Word и работа с ними](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## Настройка свойств документа в Excel  
 Для работы со встроенными свойствами в Excel используйте следующие свойства.  
  
-   В проекте на уровне документа используйте свойство <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> класса `ThisWorkbook`.  
  
-   В проекте надстройки VSTO используйте свойство <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> объекта <xref:Microsoft.Office.Interop.Excel.Workbook>.  
  
 Эти свойства возвращают объект <xref:Microsoft.Office.Core.DocumentProperties>, который представляет собой коллекцию объектов <xref:Microsoft.Office.Core.DocumentProperty>. Для извлечения конкретного свойства по имени или по индексу в коллекции можно использовать свойство `Item` коллекции.  
  
 В следующем примере кода показано, как изменить встроенное свойство **Revision Number** в проекте на уровне документа.  
  
#### Изменение свойства «Номер редакции» в Excel  
  
1.  Назначьте переменной встроенные свойства документа.  
  
     [!code-csharp[Trin_VstcoreProgramming#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#7)]
     [!code-vb[Trin_VstcoreProgramming#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#7)]  
  
2.  Увеличьте значение свойства `Revision Number` на единицу.  
  
     [!code-csharp[Trin_VstcoreProgramming#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#8)]
     [!code-vb[Trin_VstcoreProgramming#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#8)]  
  
## Настройка свойств документа в Word  
 Для работы со встроенными свойствами в Word используйте следующие свойства.  
  
-   В проекте на уровне документа используйте свойство <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> класса `ThisDocument`.  
  
-   В проекте надстройки VSTO используйте свойство <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> объекта <xref:Microsoft.Office.Interop.Word.Document>.  
  
 Эти свойства возвращают объект <xref:Microsoft.Office.Core.DocumentProperties>, который представляет собой коллекцию объектов <xref:Microsoft.Office.Core.DocumentProperty>. Для извлечения конкретного свойства по имени или по индексу в коллекции можно использовать свойство `Item` коллекции.  
  
 В следующем примере кода показано, как изменить встроенное свойство **Subject** в проекте на уровне документа.  
  
#### Изменение свойства темы  
  
1.  Назначьте переменной встроенные свойства документа.  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/VB/ThisDocument.vb#1)]  
  
2.  Измените значение свойства `Subject` на «Техническая документация».  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/VB/ThisDocument.vb#2)]  
  
## Отказоустойчивость  
 В примерах предполагается, что код написан в классе `ThisWorkbook` в проекте на уровне документа для Excel и в классе `ThisDocument` в проекте на уровне документа для Word.  
  
 Несмотря на то что вы работаете с Word и Excel и их объектами, Microsoft Office предоставляет список доступных встроенных свойств документа. В случае попытки доступа к неопределенному свойству возникает исключение.  
  
## См. также  
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Настройки программирования уровня документа](../vsto/programming-document-level-customizations.md)   
 [Практическое руководство. Создание и изменение настраиваемых свойств документа](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  