---
title: Руководство. программное использование встроенных диалоговых окон в Word
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2c3273b22d98be1c22cf0c8cea2cb57e277b9b48
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537622"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Руководство. программное использование встроенных диалоговых окон в Word
  При работе с Microsoft Office Word иногда требуется отображать диалоговые окна для ввода данных пользователем. Несмотря на то, что можно создать собственный, может потребоваться использовать встроенные диалоговые окна Word, которые представлены в <xref:Microsoft.Office.Interop.Word.Dialogs> коллекции <xref:Microsoft.Office.Interop.Word.Application> объекта. Это позволяет получить доступ к более чем 200 встроенных диалоговых окон, представленных в виде перечислений.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>Отображение диалоговых окон
 Чтобы отобразить диалоговое окно, используйте одно из значений <xref:Microsoft.Office.Interop.Word.WdWordDialog> перечисления, чтобы создать <xref:Microsoft.Office.Interop.Word.Dialog> объект, представляющий диалоговое окно, которое требуется отобразить. Затем вызовите <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> метод <xref:Microsoft.Office.Interop.Word.Dialog> объекта.

 В следующем примере кода показано, как отобразить диалоговое окно **Открытие файла** . Чтобы использовать этот пример, запустите его из `ThisDocument` класса или `ThisAddIn` в проекте.

 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Доступ к элементам диалогового окна, доступным через позднее связывание
 Некоторые свойства и методы диалоговых окон в Word доступны только через позднее связывание. Для доступа к этим членам в Visual Basic проектах, где **параметр Option-on** имеет значение ON, необходимо использовать отражение. Дополнительные сведения см. [в статье позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md).

 В следующем примере кода показано, как использовать свойство **Name** диалогового окна **открытие файла** в Visual Basic проектах, где **параметр Option** Option имеет значение OFF, или в проектах Visual C#, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Чтобы использовать этот пример, запустите его из `ThisDocument` класса или `ThisAddIn` в проекте.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 В следующем примере кода показано, как использовать отражение для доступа к свойству **Name** диалогового окна **открытие файла** в Visual Basic проектах, где **параметр Option-on** имеет значение ON. Чтобы использовать этот пример, запустите его из `ThisDocument` класса или `ThisAddIn` в проекте.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>См. также
- [Руководство. программное использование диалоговых окон Word в скрытом режиме](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Оператор Option Case](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Отражение (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection) (Отражение (Visual Basic))
