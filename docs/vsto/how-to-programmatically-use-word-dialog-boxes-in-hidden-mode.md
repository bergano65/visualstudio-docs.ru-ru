---
title: "Как: программное использование диалоговых окон Word в скрытом режиме | Документы Microsoft"
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
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
ms.assetid: a5619325-8b54-41f1-becb-3f6eae7e4a6b
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3d36bb9342c1db3fcf0fe007b87831b8c921af6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Практическое руководство. Программное использование диалоговых окон Word в скрытом режиме
  Можно выполнять сложные операции с одного вызова метода с помощью вызова встроенных диалоговых окон в Microsoft Office Word без отображения их пользователю. Это можно сделать с помощью <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> метод <xref:Microsoft.Office.Interop.Word.Dialog> объект без вызова <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> метод.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="examples"></a>Примеры  
 В следующем примере кода демонстрируется использование **параметры страницы** диалоговое окно в скрытом режиме для задания свойств нескольких страниц без участия пользователя. В примерах используется <xref:Microsoft.Office.Interop.Word.Dialog> объекта, чтобы настроить пользовательский размер страницы. Определенные параметры для настройки параметров страницы, такие как верхнее, нижнее поле и т. д., доступны как свойства позднего связывания <xref:Microsoft.Office.Interop.Word.Dialog> объекта. Эти свойства динамически создаются приложением Word во время выполнения.  
  
 В следующем примере показано, как для выполнения этой задачи в проектах Visual Basic где **Option Strict** — off и в проектах Visual C#, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. В этих проектах можно использовать компоненты позднего связывания в компиляторы Visual Basic и Visual C#. Чтобы использовать этот пример, запустите его из `ThisDocument` или `ThisAddIn` класса в проекте.  
  
 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]  
  
 В следующем примере показано, как для выполнения этой задачи в проектах Visual Basic где **Option Strict** включен. В этих проектах необходимо использовать отражение для доступа к свойствам позднего связывания. Чтобы использовать этот пример, запустите его из `ThisDocument` или `ThisAddIn` класса в проекте.  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]  
  
## <a name="see-also"></a>См. также  
 [Как: программное использование встроенных диалоговых окон в Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)   
 [Позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md)   
 [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection) (Отражение (C#))  
 [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection) (Отражение (Visual Basic))  
  
  