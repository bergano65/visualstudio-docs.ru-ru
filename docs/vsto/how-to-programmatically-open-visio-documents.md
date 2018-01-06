---
title: "Как: открытие документов Visio | Документы Microsoft"
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
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
ms.assetid: bddb820c-bde7-4d21-a0b3-6d1968baccab
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b2a6c395ed6dbfb8265ac131dd4318b590bf92e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-open-visio-documents"></a>Практическое руководство. Программное открытие документов Visio
  Существует два метода для открытия существующих документов Microsoft Office Visio: открытие и OpenEx. Метод OpenEx идентична метода открытия, за исключением того, что он содержит аргументы, в которых вызывающий объект может указать параметры открытия документа.  
  
 Подробные сведения об объектной модели см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) и метода [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) .  
  
## <a name="opening-a-visio-document"></a>Открытие документа Visio  
  
#### <a name="to-open-a-visio-document"></a>Открытие документа Visio  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Documents.Open и укажите полный путь к документу Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="opening-a-visio-document-with-specified-arguments"></a>Открытие документа Visio с заданными аргументами  
  
#### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Открытие документа Visio как закрепленного и доступного только для чтения  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Documents.OpenEx, укажите полный путь к документу Visio и включите аргументы, которые вы хотите использовать — в данном случае закрепленного и доступного только для чтения.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера кода требуется следующее.  
  
-   Документ Visio с именем `myDrawing.vsd` должен быть расположен в каталоге с именем `Test` в папке "Мои документы" (для Windows XP и более ранних версий) или в папке "Документы" (для Windows Vista).  
  
## <a name="see-also"></a>См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Общие сведения о модели объектов Visio](../vsto/visio-object-model-overview.md)   
 [Как: программное создание документов Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Как: программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Как: программное сохранение документов Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Практическое руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  