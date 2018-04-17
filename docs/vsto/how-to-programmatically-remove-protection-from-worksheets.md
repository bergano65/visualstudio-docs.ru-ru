---
title: 'Как: программное снятие защиты с листов | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c9e34e184462f1ec7822b5c2fce63aaff4a7f515
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Практическое руководство. Программное снятие защиты с листов
  Защиту с листа Microsoft Office Excel можно снять программными средствами.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 В приведенном ниже примере используется переменная `getPasswordFromUser`, которая содержит пароль, полученный от пользователя.  
  
### <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Снятие защиты с листа в настройке на уровне документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> листа, передав ему при необходимости пароль. В этом примере предполагается, что вы работаете с листом `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]  
  
### <a name="to-unprotect-a-worksheet-in-an-vsto-add-in"></a>Снятие защиты с листа в надстройке VSTO  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> активного листа, передав ему при необходимости пароль.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Как: программная Защита листов Excel](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Как: программная Защита книг Excel](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Как: программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  