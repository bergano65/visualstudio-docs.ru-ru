---
title: 'Как: программное отображение примечаний на листе | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4f7ec00b58358fb51331a40ed246e4205c206323
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Практическое руководство. Программное отображение примечаний на листе
  Вы можете отображать и скрывать комментарии в листах Microsoft Office Excel программными средствами.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Отображение всех комментариев на листе в настройке уровня документа  
  
1.  Присвойте свойству <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> значение **true** , если нужно отображать комментарии; в противном случае присвойте ему значение **false**. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Отображение всех комментариев на листе в надстройке VSTO уровня приложения  
  
1.  Присвойте свойству <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> значение **true** , если нужно отображать комментарии; в противном случае присвойте ему значение **false**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Как: программное добавление и удаление примечаний на листе](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)  
  
  