---
title: Как выполнить Программное снятие защиты с листов
ms.date: 02/02/2017
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
ms.openlocfilehash: cd0aacdd168c65cda9f7ac57880e3216b3fb3daa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956144"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Как выполнить Программное снятие защиты с листов
  Защиту с листа Microsoft Office Excel можно снять программными средствами.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 В приведенном ниже примере используется переменная `getPasswordFromUser`, которая содержит пароль, полученный от пользователя.  
  
## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Снятие защиты с листа в настройке на уровне документа  
  
1.  Вызовите <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> метод листа, передав ему при необходимости пароль. В этом примере предполагается, что вы работаете с листом `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]  
  
## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Снятие защиты с листа в надстройке VSTO  
  
1.  Вызовите <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> метод активного листа, передав ему при необходимости пароль.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Практическое руководство. Программная Защита листов Excel](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Практическое руководство. Программная Защита книг Excel](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Практическое руководство. Программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)  
