---
title: "Практическое руководство. Программное использование встроенных диалоговых окон в Word"
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
  - "Word [разработка решений Office в Visual Studio], диалоговые окна"
  - "диалоговые окна, Word"
ms.assetid: 0c7e4338-dead-4444-868b-3b0212368455
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Практическое руководство. Программное использование встроенных диалоговых окон в Word
  При работе с Microsoft Office Word бывают ситуации, когда нужно отобразить диалоговые окна для ввода пользователя.  Хотя можно использовать собственный подход, может также понадобиться использовать подход с использованием диалоговых окон, встроенных в Word и представленных в коллекции <xref:Microsoft.Office.Interop.Word.Dialogs> объекта <xref:Microsoft.Office.Interop.Word.Application>.  Это дает возможность доступа к более чем к 200 встроенным диалоговым окнам, представленным как перечисления.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Отображение диалоговых окон  
 Чтобы отобразить диалоговое окно, используйте одно из значений перечисления <xref:Microsoft.Office.Interop.Word.WdWordDialog> для создания объекта <xref:Microsoft.Office.Interop.Word.Dialog>, представляющего диалоговое окно, которое нужно отобразить.  Затем вызовите метод <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> объекта <xref:Microsoft.Office.Interop.Word.Dialog>.  
  
 В следующем примере кода показано, как вывести на экран диалоговое окно**Открытие файла**.  Чтобы использовать следующий пример кода, запустите его в проекте из класса `ThisDocument` или `ThisAddIn`.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#100](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreWordAutomation#100](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#100)]  
  
### Доступ к элементам диалоговых окон, доступным только через позднее связывание  
 Некоторые свойства и методы диалоговых окон доступны только с помощью позднего связывания.  В проектах Visual Basic, где параметр **Option Strict** включен, необходимо использовать отражение для доступа к этим членам.  Дополнительные сведения см. в разделе [Позднее связывание в решениях Office](../vsto/late-binding-in-office-solutions.md).  
  
 В следующем примере кода демонстрируется использование свойства **Name** диалогового окна **Открытие файла** в проектах Visual Basic, **Option Strict** из или в проектах Visual C\# \- \#, целевой объект [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)].  Чтобы использовать следующий пример кода, запустите его в проекте из класса `ThisDocument` или `ThisAddIn`.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 В следующем примере кода показано, как использовать отражение для доступа к свойству **Name** диалогового окна **Открытие файла** в проектах Visual Basic, где параметр **Option Strict** включен.  Чтобы использовать следующий пример кода, запустите его в проекте из класса `ThisDocument` или `ThisAddIn`.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## См. также  
 [Практическое руководство. Программное использование диалоговых окон Word в скрытом режиме](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Отражение &#40;C&#35; и Visual Basic&#41;](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)  
  
  