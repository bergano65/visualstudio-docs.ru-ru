---
title: Практическое руководство. Программное использование встроенных диалоговых окон в Word
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: f8037e4d91aa7706c7ffd7b9f32778dfeac79488
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644943"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Практическое руководство. Программное использование встроенных диалоговых окон в Word
  При работе с Microsoft Office Word, бывают случаи, при необходимости отображать диалоговые окна для ввода данных пользователем. Несмотря на то, что вы можете создать свой собственный, можно использовать подход с использованием встроенных диалоговых окон в Word, которые представлены на <xref:Microsoft.Office.Interop.Word.Dialogs> коллекцию <xref:Microsoft.Office.Interop.Word.Application> объекта. Это позволяет получить доступ к более чем 200 встроенных диалоговых окон, которые представлены в виде перечисления.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>Отображение диалоговых окон
 Чтобы отобразить диалоговое окно, используйте одно из значений из <xref:Microsoft.Office.Interop.Word.WdWordDialog> перечисления для создания <xref:Microsoft.Office.Interop.Word.Dialog> объект, представляющий окно будет отображаться. Затем вызовите <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> метод <xref:Microsoft.Office.Interop.Word.Dialog> объекта.

 В следующем примере кода показано, как отобразить **Открытие файла** диалоговое окно. Чтобы использовать этот пример, запустите его из `ThisDocument` или `ThisAddIn` в своем проекте.

 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Доступа к элементам диалогового окна, доступные через позднее связывание
 Некоторые свойства и методы диалоговых окон в Word доступны только через позднее связывание. В проектах Visual Basic where **Option Strict** имеет значение on, следует использовать отражение для доступа к этим членам. Дополнительные сведения см. в разделе [позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md).

 В следующем примере кода демонстрируется использование **имя** свойство **Открытие файла** диалоговое окно в Visual Basic проецирует where **Option Strict** отключена или в Visual C# проекты, предназначенные [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Чтобы использовать этот пример, запустите его из `ThisDocument` или `ThisAddIn` в своем проекте.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 В следующем примере кода показано, как использовать отражение для доступа к **имя** свойство **Открытие файла** диалоговое окно в Visual Basic проецирует where **Option Strict** — в. Чтобы использовать этот пример, запустите его из `ThisDocument` или `ThisAddIn` в своем проекте.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>См. также
- [Практическое руководство. Программное использование диалоговых окон Word в скрытом режиме](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Обзор объектной модели Word](../vsto/word-object-model-overview.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Оператор Option strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection) (Отражение (C#))
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection) (Отражение (Visual Basic))
