---
title: "Как: Добавление пользовательских XML-частей в документы с помощью надстроек VSTO | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b2c9fec7370e5b4f9bab8ac7773ba1a18f36d261
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Практическое руководство. Добавление пользовательских XML-частей в документы с помощью надстроек VSTO
  XML-данные можно сохранить в следующих типах документов, создав пользовательскую XML-часть в надстройке VSTO:  
  
-   книга Microsoft Office Excel;  
  
-   документ Microsoft Office Word;  
  
-   презентация Microsoft Office PowerPoint.  
  
 Для получения дополнительной информации см. [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md).  
  
 **Область применения.** Сведения этого раздела относятся к проектам уровня приложения для Excel, PowerPoint и Word. Дополнительные сведения см. в разделе [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Добавление пользовательской XML-части в книгу Excel  
  
1.  Добавьте новый объект <xref:Microsoft.Office.Core.CustomXMLPart> в коллекцию <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> в книге. Объект <xref:Microsoft.Office.Core.CustomXMLPart> содержит XML-строку, которую требуется сохранить в книге.  
  
     Следующий пример кода добавляет пользовательскую XML-часть в указанную книгу.  
  
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]  
  
2.  Добавьте метод `AddCustomXmlPartToWorkbook` в класс `ThisAddIn` в проекте надстройки VSTO для Excel.  
  
3.  Вызовите метод из другого кода в проекте. Например, для создания пользовательской XML-части, когда пользователь открывает книгу, вызовите метод из обработчика события <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> .  
  
### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Добавление пользовательской XML-части в документ Word  
  
1.  Добавьте новый объект <xref:Microsoft.Office.Core.CustomXMLPart> в коллекцию <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> в документе. Объект <xref:Microsoft.Office.Core.CustomXMLPart> содержит XML-строку, которую требуется сохранить в документе.  
  
     Следующий пример кода добавляет пользовательскую XML-часть в указанный документ.  
  
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]  
  
2.  Добавьте метод `AddCustomXmlPartToDocument` в класс `ThisAddIn` в проекте надстройки VSTO для Word.  
  
3.  Вызовите метод из другого кода в проекте. Например, для создания пользовательской XML-части, когда пользователь открывает документ, вызовите метод из обработчика события <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .  
  
### <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>Добавление пользовательской XML-части в презентацию PowerPoint  
  
1.  Добавьте новый объект <xref:Microsoft.Office.Core.CustomXMLPart> в коллекцию <xref:Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts%2A> в презентации. Объект <xref:Microsoft.Office.Core.CustomXMLPart> содержит XML-строку, которую требуется сохранить в презентации.  
  
     Следующий пример кода добавляет пользовательскую XML-часть в указанную презентацию.  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]  
  
2.  Добавьте метод `AddCustomXmlPartToPresentation` в класс `ThisAddIn` в проекте надстройки VSTO для PowerPoint.  
  
3.  Вызовите метод из другого кода в проекте. Например, для создания пользовательской XML-части, когда пользователь открывает презентацию, вызовите метод из обработчика события <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen> .  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Для простоты в этом примере используется XML-строка, которая определена как локальная переменная в методе. Обычно следует получать XML из внешнего источника, например файла или базы данных.  
  
## <a name="see-also"></a>См. также  
 [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md)   
 [Практическое руководство. Добавление настраиваемых частей XML в настройках уровня документа](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  