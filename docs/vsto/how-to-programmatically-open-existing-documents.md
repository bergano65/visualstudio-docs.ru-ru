---
title: "Как: Открытие существующих документов | Документы Microsoft"
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
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 151571ace6790f05c067f8dff641988301bc1b0e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-open-existing-documents"></a>Практическое руководство. Программное открытие существующих документов
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> Метод открывает существующий документ Microsoft Office Word, заданный параметром полный путь и имя файла. Этот метод возвращает <xref:Microsoft.Office.Interop.Word.Document> , представляющий открытый документ.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-open-a-document"></a>Чтобы открыть документ  
  
-   Вызовите <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> метод <xref:Microsoft.Office.Interop.Word.Documents> коллекции и предоставьте путь к документу.  
  
     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]  
  
### <a name="to-open-a-document-as-read-only"></a>Чтобы открыть документ только для чтения  
  
-   Вызовите <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> метод, укажите путь к документу и задайте *ReadOnly* аргумент **True** в вызове метода.  
  
     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера кода требуется следующее.  
  
-   Должен существовать документ NewDocument.doc в каталоге с именем Test на диске C.  
  
## <a name="see-also"></a>См. также  
 [Как: программное создание документов](../vsto/how-to-programmatically-create-new-documents.md)   
 [Как: программное закрытие документов](../vsto/how-to-programmatically-close-documents.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  