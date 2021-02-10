---
title: Руководство. Программное открытие существующих документов
description: Узнайте, как использовать метод Open для открытия существующего документа Microsoft Word, заданного с помощью полного пути и имени файла.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 81d134c88d93b3da3b0f0e6c3ded3cbe0d6d3f89
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951684"
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

## <a name="see-also"></a>См. также раздел
- [Руководство. Программное создание новых документов](../vsto/how-to-programmatically-create-new-documents.md)
- [Руководство. программное закрытие документов](../vsto/how-to-programmatically-close-documents.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
