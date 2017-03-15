---
title: "Практическое руководство. Использование области анимации в строке состояния | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "строка состояния, программирование"
  - "строка состояния, область анимации"
  - "область анимации, строка состояния"
ms.assetid: ec6fb915-7bc8-4a90-8156-70c1a243caff
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Практическое руководство. Использование области анимации в строке состояния
Область анимации  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в строке состояния отображается анимированный значок циклическое, которая показывает или длинномерную операцию операцию или непредвиденной длины \(например, построение нескольких проектов в решении\).  
  
### Использовать область анимации в строке состояния Visual Studio  
  
1.  Получение экземпляра <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> интерфейс, который становится доступным через  <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> служба.  
  
2.  Запускает анимацию путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A> метод строки состояния.  Передайте 1 в качестве значения первого параметра и ссылку на оживленному значок в качестве значения второго параметра.  
  
3.  Останавливает анимацию путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A> метод строки состояния.  Передайте 0 в качестве значения первого параметра и ссылку на оживленному значок в качестве значения второго параметра.  
  
## Пример  
 В этом примере показано, как выполнить встроенную анимация в области анимации.  
  
 [!CODE [VSSDKAnimationStatusBar#1](../CodeSnippet/VS_Snippets_VSSDK/vssdkanimationstatusbar#1)]  
  
## См. также  
 [Расширение строки состояния](../extensibility/extending-the-status-bar.md)   
 [Практическое руководство. Чтение и запись в области обратной связи в строке состояния](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [Практическое руководство. Программирование области хода выполнения в строке состояния](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [Практическое руководство. Программирование области конструктора в строке состояния](../Topic/How%20to:%20Program%20the%20Designer%20Region%20of%20the%20Status%20Bar.md)