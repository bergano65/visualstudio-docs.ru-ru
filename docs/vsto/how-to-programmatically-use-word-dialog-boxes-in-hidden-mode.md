---
title: "Практическое руководство. Программное использование диалоговых окон Word в скрытом режиме | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "диалоговые окна, скрытый режим в Word"
  - "скрытые диалоговые окна"
  - "Word [разработка решений Office в Visual Studio], диалоговые окна"
ms.assetid: a5619325-8b54-41f1-becb-3f6eae7e4a6b
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Практическое руководство. Программное использование диалоговых окон Word в скрытом режиме
  Можно выполнять сложные операции на встроенных диалоговых окнах Microsoft Office Word посредством вызова одного метода, не показывая эти окна пользователю.  Используйте для этого метод <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> объекта <xref:Microsoft.Office.Interop.Word.Dialog>, не вызывая метод <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A>.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Примеры  
 В следующих примерах кода демонстрируется использование диалогового окна **Настройка страницы** в скрытом режиме для задания свойств нескольких страниц без ввода информации пользователем.  Для настройки пользовательского размера страницы в примерах используется объект <xref:Microsoft.Office.Interop.Word.Dialog>.  Указанные параметры — TopMargin \(верхнее поле\), BottomMargin \(нижнее поле\) и т. д. — доступны в качестве свойств с поздним связыванием объекта <xref:Microsoft.Office.Interop.Word.Dialog>.  Эти свойства динамически создаются приложением Word во время выполнения.  
  
 В следующем примере показано выполнение этой задачи в проектах Visual Basic с выключенным параметром **Option Strict** и в проектах Visual C\# для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  В этих проектах возможно изменение функций позднего связывания для компиляторов Visual Basic и Visual C\#.  Чтобы использовать следующий пример кода, запустите его в проекте из класса `ThisDocument` или `ThisAddIn`.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#123](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#123)]
 [!code-vb[Trin_VstcoreWordAutomation#123](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#123)]  
  
 В следующем примере показано выполнение этой задачи в проектах Visual Basic, где **Option Strict** on.  В этих проектах для доступа к свойствам с поздним связыванием необходимо использовать отражение.  Чтобы использовать следующий пример кода, запустите его в проекте из класса `ThisDocument` или `ThisAddIn`.  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#104)]  
  
## См. также  
 [Практическое руководство. Программное использование встроенных диалоговых окон в Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)   
 [Позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md)   
 [Отражение &#40;C&#35; и Visual Basic&#41;](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)  
  
  