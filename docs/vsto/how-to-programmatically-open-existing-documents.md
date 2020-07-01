---
title: Руководство. Программное открытие существующих документов
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eba4d110b06147db384a4d7aafe01c7d9f272ba3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85519903"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Руководство. Программное открытие существующих документов
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>Метод открывает существующий Microsoft Office документ Word, указанный в полном пути и имени файла. Этот метод возвращает объект <xref:Microsoft.Office.Interop.Word.Document> , представляющий открытый документ.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Открытие документа

- Вызовите <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> метод <xref:Microsoft.Office.Interop.Word.Documents> коллекции и укажите путь к документу.

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>Открытие документа только для чтения

- Вызовите <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> метод, укажите путь к документу и задайте для аргумента *ReadOnly* в вызове метода **значение true** .

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера кода требуется следующее.

- Документ с именем *NewDocument.doc* должен существовать в каталоге с именем *Test* на диске C.

## <a name="see-also"></a>См. также
- [Руководство. Программное создание новых документов](../vsto/how-to-programmatically-create-new-documents.md)
- [Руководство. программное закрытие документов](../vsto/how-to-programmatically-close-documents.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
