---
title: 'Как: Добавление пользовательских XML-частей в настройках уровня документа | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document-level customizations [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5126e5ca6eb83df70ed03a7491fdd5d2a98912e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Практическое руководство. Добавление пользовательских XML-частей в настройках уровня документа
  XML-данные можно сохранять в книге Microsoft Office Excel или документе Microsoft Office Word путем создания настраиваемой XML-части в настройке на уровне документа. Для получения дополнительной информации см. [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Visual Studio не предоставляет проекты уровня документа для Microsoft Office PowerPoint. Сведения о добавлении пользовательской XML-части в презентацию PowerPoint с использованием надстройки VSTO см. в разделе [как: Добавление пользовательских XML-частей в документы с помощью надстроек VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).  
  
### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Добавление пользовательской XML-части в книгу Excel  
  
1.  Добавьте новый объект <xref:Microsoft.Office.Core.CustomXMLPart> в коллекцию <xref:Microsoft.Office.Core.CustomXMLParts> в книге. Объект <xref:Microsoft.Office.Core.CustomXMLPart> содержит XML-строку, которую требуется сохранить в книге.  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb#1)]  
  
2.  Добавьте метод `AddCustomXmlPartToWorkbook` в класс `ThisWorkbook` в проекте уровня документа для Excel.  
  
3.  Вызовите метод из другого кода в проекте. Например, для создания настраиваемой XML-части, когда пользователь открывает книгу, вызовите метод из обработчика событий `ThisWorkbook_Startup` .  
  
### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Добавление пользовательской XML-части в документ Word  
  
1.  Добавьте новый объект <xref:Microsoft.Office.Core.CustomXMLPart> в коллекцию <xref:Microsoft.Office.Core.CustomXMLParts> в документе. Объект <xref:Microsoft.Office.Core.CustomXMLPart> содержит XML-строку, которую требуется сохранить в документе.  
  
     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs#1)]  
  
2.  Добавьте метод `AddCustomXmlPartToDocument` в класс `ThisDocument` в проекте уровня документа для Word.  
  
3.  Вызовите метод из другого кода в проекте. Например, для создания настраиваемой XML-части, когда пользователь открывает документ, вызовите метод из обработчика событий `ThisDocument_Startup` .  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Для простоты в этом примере используется XML-строка, которая определена как локальная переменная в методе. Обычно следует получать XML из внешнего источника, например файла или базы данных.  
  
## <a name="see-also"></a>См. также  
 [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md)   
 [Практическое руководство. Добавление настраиваемых частей XML в документы с помощью надстроек VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
  