---
title: Как выполнить Программное Открытие существующих документов
ms.date: 02/02/2017
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
ms.openlocfilehash: 2163ddc7db3f0fbcf32abaa8c845b3838e9d2c98
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932159"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Как выполнить Программное Открытие существующих документов
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> Метод открывает существующий документ Microsoft Office Word, заданный параметром полный путь и имя файла. Этот метод возвращает <xref:Microsoft.Office.Interop.Word.Document> , представляющий открытый документ.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-open-a-document"></a>Чтобы открыть документ  
  
-   Вызовите <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> метод <xref:Microsoft.Office.Interop.Word.Documents> коллекции и предоставьте путь к документу.  
  
     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]  
  
## <a name="to-open-a-document-as-read-only"></a>Чтобы открыть документ только для чтения  
  
-   Вызовите <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> метод, укажите путь к документу и задать *ReadOnly* аргумент **True** в вызове метода.  
  
     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 Для этого примера кода требуется следующее.  
  
-   Документ с именем *NewDocument.doc* должен существовать в каталог с именем *теста* на диске C.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Программное создание документов](../vsto/how-to-programmatically-create-new-documents.md)   
 [Практическое руководство. Программное закрытие документов](../vsto/how-to-programmatically-close-documents.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
