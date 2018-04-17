---
title: 'Как: программным образом сброс диапазонов в документах Word | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ed267f4ed2211f2dda69b620aec9fdadbe5a76c2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>Практическое руководство. Программный сброс диапазонов в документах Word
  Используйте метод <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> для изменения размеров существующего диапазона в документе Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-reset-an-existing-range"></a>Сброс существующего диапазона  
  
1.  Установите исходный диапазон, начиная с первых семи знаков в документе.  
  
     Следующий пример кода можно использовать в настройке на уровне документа.  
  
     [!code-vb[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#43)]  
  
     Приведенный ниже пример кода можно использовать в надстройке VSTO. В этом примере кода используется активный документ.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#43)]  
  
2.  Используйте <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> для начала диапазона во втором предложении и завершения его в конце пятого предложения.  
  
     [!code-vb[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#44)]
     [!code-csharp[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#44)]  
  
## <a name="document-level-customization-example"></a>Пример настройки на уровне документа  
  
#### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>Сброс существующего диапазона в настройке уровня документа  
  
1.  В следующем примере показан полный код для настройки уровня документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#42)]  
  
## <a name="vsto-add-in-example"></a>Примеры надстройки VSTO  
  
#### <a name="to-reset-an-existing-range-in-an-vsto-add-in"></a>Сброс существующего диапазона в надстройке VSTO  
  
1.  В следующем примере показан полный код для надстройки VSTO. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#42)]  
  
## <a name="see-also"></a>См. также  
 [Как: программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Как: программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Как: программное извлечение символов начала и завершения в диапазонах](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Практическое руководство. Программное свертывание диапазонов и выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)  
  
  