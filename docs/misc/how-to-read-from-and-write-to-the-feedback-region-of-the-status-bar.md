---
title: "Практическое руководство. Чтение и запись в области обратной связи в строке состояния | Microsoft Docs"
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
  - "область обратной связи, строка состояния"
  - "строка состояния, область обратной связи"
  - "строка состояния, обзор"
ms.assetid: e639561c-e1e7-4660-b2a2-8bca80f34a29
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Практическое руководство. Чтение и запись в области обратной связи в строке состояния
Область отзывов и предложений [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] отображает текст строки состояния.  Можно установить и получить текст, отображаемый текст является статическим и выберите текст, который отображается.  
  
### Использовать область отзывов и предложения строки состояния Visual Studio  
  
1.  Получение экземпляра <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> интерфейс, который становится доступным через  <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> служба.  
  
2.  Укажите, является замороженной, является ли строка состояния, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A> метод   <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> экземпляр.  
  
3.  Задайте текст области отзывов и предложения, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.SetText%2A> метод и передачи в текстовую строку.  
  
4.  Чтение текста области отзывов и предложения, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A> метод.  
  
## Пример  
 Этот пример показывает, как записать текст и чтение текста из области отзывов и предложений.  
  
 [!code-cs[VSSDKFeedbackStatusBar#1](../misc/codesnippet/CSharp/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.cs)]
 [!code-vb[VSSDKFeedbackStatusBar#1](../misc/codesnippet/VisualBasic/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.vb)]  
  
 В приведенном выше примере код выполняет следующие действия:  
  
-   Возвращает экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> интерфейс из  <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> служба.  
  
-   Проверяет, если строка состояния является замороженной, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A> метод.  
  
-   Блокирует дальнейшие обновлений в строке состояния путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A> метод.  
  
-   Чтение текста из строки состояния, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A> метод и отображает его в окне сообщения.  
  
-   Разрешает обновления к строке состояния путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A> и передача 0 в параметре.  
  
-   Удаляет содержимое строки состояния, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Clear%2A> метод.  
  
## См. также  
 [Расширение строки состояния](../extensibility/extending-the-status-bar.md)   
 [Практическое руководство. Программирование области хода выполнения в строке состояния](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [Практическое руководство. Использование области анимации в строке состояния](../misc/how-to-use-the-animation-region-of-the-status-bar.md)   
 [Практическое руководство. Программирование области конструктора в строке состояния](../Topic/How%20to:%20Program%20the%20Designer%20Region%20of%20the%20Status%20Bar.md)