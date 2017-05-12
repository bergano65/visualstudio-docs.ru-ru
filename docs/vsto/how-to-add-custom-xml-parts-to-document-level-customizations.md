---
title: "Практическое руководство. Добавление пользовательских XML-частей в настройках уровня документа"
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
  - "настройки на уровне документа [разработка решений Office в Visual Studio], настраиваемые XML-части"
  - "документы Office [разработка решений Office в Visual Studio], настраиваемые XML-части"
  - "Word [разработка решений Office в Visual Studio], настраиваемые XML-части"
  - "Excel [разработка решений Office в Visual Studio], настраиваемые XML-части"
  - "настраиваемые XML-части [разработка решений Office в Visual Studio], добавление"
  - "документы [разработка решений Office в Visual Studio], настраиваемые XML-части"
ms.assetid: e305a3d6-3a0e-4e72-ab8c-6a87a3590068
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Практическое руководство. Добавление пользовательских XML-частей в настройках уровня документа
  XML\-данные можно сохранять в книге Microsoft Office Excel или документе Microsoft Office Word путем создания настраиваемой XML\-части в настройке на уровне документа. Для получения дополнительной информации см. [Общие сведения о пользовательских XML-частях](../vsto/custom-xml-parts-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Visual Studio не предоставляет проекты уровня документа для Microsoft Office PowerPoint. Сведения о добавлении настраиваемой XML\-части в презентацию PowerPoint с использованием надстройки VSTO см. в разделе [Практическое руководство. Добавление пользовательских XML-частей в документы с помощью надстроек VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).  
  
### Добавление пользовательской XML\-части в книгу Excel  
  
1.  Добавьте новый объект <xref:Microsoft.Office.Core.CustomXMLPart> в коллекцию <xref:Microsoft.Office.Core.CustomXMLParts> в книге. Объект <xref:Microsoft.Office.Core.CustomXMLPart> содержит XML\-строку, которую требуется сохранить в книге.  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelDocLevel/CS/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelDocLevel/VB/ThisWorkbook.vb#1)]  
  
2.  Добавьте метод `AddCustomXmlPartToWorkbook` в класс `ThisWorkbook` в проекте уровня документа для Excel.  
  
3.  Вызовите метод из другого кода в проекте. Например, для создания настраиваемой XML\-части, когда пользователь открывает книгу, вызовите метод из обработчика событий `ThisWorkbook_Startup`.  
  
### Добавление пользовательской XML\-части в документ Word  
  
1.  Добавьте новый объект <xref:Microsoft.Office.Core.CustomXMLPart> в коллекцию <xref:Microsoft.Office.Core.CustomXMLParts> в документе. Объект <xref:Microsoft.Office.Core.CustomXMLPart> содержит XML\-строку, которую требуется сохранить в документе.  
  
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordDocLevel/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordDocLevel/VB/ThisDocument.vb#1)]  
  
2.  Добавьте метод `AddCustomXmlPartToDocument` в класс `ThisDocument` в проекте уровня документа для Word.  
  
3.  Вызовите метод из другого кода в проекте. Например, для создания настраиваемой XML\-части, когда пользователь открывает документ, вызовите метод из обработчика событий `ThisDocument_Startup`.  
  
## Отказоустойчивость  
 Для простоты в этом примере используется XML\-строка, которая определена как локальная переменная в методе. Обычно следует получать XML из внешнего источника, например файла или базы данных.  
  
## См. также  
 [Общие сведения о пользовательских XML-частях](../vsto/custom-xml-parts-overview.md)   
 [Практическое руководство. Добавление пользовательских XML-частей в документы с помощью надстроек VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
  