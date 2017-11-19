---
title: "Как: программное использование встроенных диалоговых окон в Word | Документы Microsoft"
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
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
ms.assetid: 0c7e4338-dead-4444-868b-3b0212368455
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7dd7d81837699aedd1c6c61d0cb0d9e2e9a64db4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Практическое руководство. Программное использование встроенных диалоговых окон в Word
  При работе с Microsoft Office Word, бывают ситуации, при необходимости отображать диалоговые окна для ввода данных пользователем. Несмотря на то, что вы можете создать собственные, также можно использовать подход с использованием встроенных диалоговых окон в Word, представленных в <xref:Microsoft.Office.Interop.Word.Dialogs> коллекцию <xref:Microsoft.Office.Interop.Word.Application> объекта. Это позволяет получить доступ к более чем 200 встроенных диалоговых окон, которые представлены в виде перечисления.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="displaying-dialog-boxes"></a>Отображение диалоговых окон  
 Чтобы отобразить диалоговое окно, используйте одно из значений <xref:Microsoft.Office.Interop.Word.WdWordDialog> перечисления для создания <xref:Microsoft.Office.Interop.Word.Dialog> объект, представляющий окно для отображения. Затем вызовите метод <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> метод <xref:Microsoft.Office.Interop.Word.Dialog> объекта.  
  
 В следующем примере кода показано, как отобразить **Открытие файла** диалоговое окно. Чтобы использовать этот пример, запустите его из `ThisDocument` или `ThisAddIn` класса в проекте.  
  
 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]  
  
### <a name="accessing-dialog-box-members-that-are-available-through-late-binding"></a>Доступ к элементам диалогового окна, доступные через позднее связывание  
 Некоторые свойства и методы диалоговых окон в Word доступны только с помощью позднего связывания. В проектах Visual Basic where **Option Strict** имеет значение on, необходимо использовать отражение для доступа к этим элементам. Дополнительные сведения см. в разделе [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md).  
  
 В следующем примере кода демонстрируется использование **имя** свойство **Открытие файла** диалоговое окно в Visual Basic проекты where **Option Strict** выключен или находится в Visual C# проекты, предназначенные [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Чтобы использовать этот пример, запустите его из `ThisDocument` или `ThisAddIn` класса в проекте.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 В следующем примере кода показано, как использовать отражение для доступа к **имя** свойство **Открытие файла** диалоговое окно в Visual Basic проекты where **Option Strict** — в. Чтобы использовать этот пример, запустите его из `ThisDocument` или `ThisAddIn` класса в проекте.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>См. также  
 [Как: программное использование диалоговых окон Word в скрытом режиме](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection) (Отражение (C#))  
 [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection) (Отражение (Visual Basic))  
  
  