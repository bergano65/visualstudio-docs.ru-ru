---
title: Практическое руководство. Программное использование диалоговых окон Word в скрытом режиме
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e7a422e9548fabefa2066fb439c01e382586cd36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961609"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Практическое руководство. Программное использование диалоговых окон Word в скрытом режиме
  Можно выполнять сложные операции с помощью одного вызова метода путем вызова встроенных диалоговых окон в Microsoft Office Word без отображения их пользователю. Это можно сделать с помощью <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> метод <xref:Microsoft.Office.Interop.Word.Dialog> объекта без вызова <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> метод.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Примеры
 В следующих примерах кода демонстрируется использование **параметры страницы** диалоговое окно в скрытом режиме для задания свойств нескольких страниц без участия пользователя. В примерах используется <xref:Microsoft.Office.Interop.Word.Dialog> настройте пользовательский размер страницы. Определенные параметры для настройки параметров страницы, такие как верхнее, нижнее поле и т. д., доступны как свойства с поздним связыванием <xref:Microsoft.Office.Interop.Word.Dialog> объекта. Эти свойства динамически создаются в Word во время выполнения.

 В следующем примере показано, как для выполнения этой задачи в проектах Visual Basic где **Option Strict** — off и в проектах Visual C#, предназначенных [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. В этих проектах можно использовать компоненты позднего связывания в компиляторы Visual Basic и Visual C#. Чтобы использовать этот пример, запустите его из `ThisDocument` или `ThisAddIn` в своем проекте.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 В следующем примере показано, как для выполнения этой задачи в проектах Visual Basic где **Option Strict** включен. В этих проектах необходимо использовать отражение для доступа к свойствам с поздним связыванием. Чтобы использовать этот пример, запустите его из `ThisDocument` или `ThisAddIn` в своем проекте.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>См. также
- [Практическое руководство. Программное использование встроенных диалоговых окон в Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Обзор объектной модели Word](../vsto/word-object-model-overview.md)
- [Позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md)
- [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection) (Отражение (C#))
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection) (Отражение (Visual Basic))
