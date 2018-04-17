---
title: 'Как: Открытие существующих документов | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0c7542b2222839afc75b3b5b1b84fc5afe56f523
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
  