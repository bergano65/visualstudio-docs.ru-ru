---
title: "Практическое руководство. Добавление пользовательских XML-частей в документы с помощью надстроек VSTO | Microsoft Docs"
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
  - "надстройки [разработка решений Office в Visual Studio], настраиваемые XML-части"
  - "документы Office [разработка решений Office в Visual Studio], настраиваемые XML-части"
  - "Word [разработка решений Office в Visual Studio], настраиваемые XML-части"
  - "PowerPoint [разработка решений Office в Visual Studio], настраиваемые XML-части"
  - "Excel [разработка решений Office в Visual Studio], настраиваемые XML-части"
  - "настраиваемые XML-части [разработка решений Office в Visual Studio], добавление"
  - "документы [разработка решений Office в Visual Studio], настраиваемые XML-части"
  - "надстройки уровня приложения [разработка решений Office в Visual Studio], настраиваемые XML-части"
ms.assetid: 872d2beb-193b-49f9-9a7b-dcebab91a73b
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Практическое руководство. Добавление пользовательских XML-частей в документы с помощью надстроек VSTO
  XML\-данные можно сохранить в следующих типах документов, создав пользовательскую XML\-часть в надстройке VSTO:  
  
-   книга Microsoft Office Excel;  
  
-   документ Microsoft Office Word;  
  
-   презентация Microsoft Office PowerPoint.  
  
 Для получения дополнительной информации см. [Общие сведения о пользовательских XML-частях](../vsto/custom-xml-parts-overview.md).  
  
 **Область применения.** Сведения этого раздела относятся к проектам уровня приложения для Excel, PowerPoint и Word. Для получения дополнительной информации см. [Доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).  
  
### Добавление пользовательской XML\-части в книгу Excel  
  
1.  Добавьте новый объект <xref:Microsoft.Office.Core.CustomXMLPart> в коллекцию <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> в книге. Объект <xref:Microsoft.Office.Core.CustomXMLPart> содержит XML\-строку, которую требуется сохранить в книге.  
  
     Следующий пример кода добавляет пользовательскую XML\-часть в указанную книгу.  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Добавьте метод `AddCustomXmlPartToWorkbook` в класс `ThisAddIn` в проекте надстройки VSTO для Excel.  
  
3.  Вызовите метод из другого кода в проекте. Например, для создания пользовательской XML\-части, когда пользователь открывает книгу, вызовите метод из обработчика события <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen>.  
  
### Добавление пользовательской XML\-части в документ Word  
  
1.  Добавьте новый объект <xref:Microsoft.Office.Core.CustomXMLPart> в коллекцию <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> в документе. Объект <xref:Microsoft.Office.Core.CustomXMLPart> содержит XML\-строку, которую требуется сохранить в документе.  
  
     Следующий пример кода добавляет пользовательскую XML\-часть в указанный документ.  
  
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Добавьте метод `AddCustomXmlPartToDocument` в класс `ThisAddIn` в проекте надстройки VSTO для Word.  
  
3.  Вызовите метод из другого кода в проекте. Например, для создания пользовательской XML\-части, когда пользователь открывает документ, вызовите метод из обработчика события <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.  
  
### Добавление пользовательской XML\-части в презентацию PowerPoint  
  
1.  Добавьте новый объект <xref:Microsoft.Office.Core.CustomXMLPart> в коллекцию <xref:Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts%2A> в презентации. Объект <xref:Microsoft.Office.Core.CustomXMLPart> содержит XML\-строку, которую требуется сохранить в презентации.  
  
     Следующий пример кода добавляет пользовательскую XML\-часть в указанную презентацию.  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartPowerPointAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartPowerPointAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Добавьте метод `AddCustomXmlPartToPresentation` в класс `ThisAddIn` в проекте надстройки VSTO для PowerPoint.  
  
3.  Вызовите метод из другого кода в проекте. Например, для создания пользовательской XML\-части, когда пользователь открывает презентацию, вызовите метод из обработчика события <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen>.  
  
## Отказоустойчивость  
 Для простоты в этом примере используется XML\-строка, которая определена как локальная переменная в методе. Обычно следует получать XML из внешнего источника, например файла или базы данных.  
  
## См. также  
 [Общие сведения о пользовательских XML-частях](../vsto/custom-xml-parts-overview.md)   
 [Практическое руководство. Добавление пользовательских XML-частей в настройках уровня документа](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  