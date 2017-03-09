---
title: "Практическое руководство. Программирование области хода выполнения в строке состояния | Microsoft Docs"
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
  - "строка состояния, область индикатора выполнения"
  - "индикатор выполнения, строка состояния"
  - "строка состояния, программирование"
ms.assetid: 4b54616a-8c20-436d-b764-f2380e5760f2
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# Практическое руководство. Программирование области хода выполнения в строке состояния
Область применения индикатора выполнения [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в строке состояния отображается знак " плюс ход выполнения операций быстрой, например, сохранение файла на диск.  
  
### Использовать область индикатора выполнения строки состояния Visual Studio  
  
1.  Получение экземпляра <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> интерфейс, который становится доступным через  <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> служба.  
  
2.  Инициализация индикатор выполнения на запуск значения путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> метод.  
  
3.  Обновите индикатор выполнения отвечает за вызов операции продолжается с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> метод, чтобы установить новые значения.  
  
## Пример  
 В этом примере показано, как инициализировать и обновления индикатора выполнения.  
  
 [!CODE [VSSDKProgressStatusBar#1](../CodeSnippet/VS_Snippets_VSSDK/vssdkprogressstatusbar#1)]  
  
 В этом примере код:  
  
-   Возвращает экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> интерфейс из  <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> служба.  
  
-   Инициализирует индикатор выполнения, заданного для запуска значения путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> метод.  
  
-   Имитирует операцию путем прохода через a <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> цикл и обновления значений индикатора выполнения с помощью  `for` метод.  
  
-   Очищает индикатор выполнения с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Clear%2A> метод.  
  
## См. также  
 [Расширение строки состояния](../extensibility/extending-the-status-bar.md)   
 [Практическое руководство. Чтение и запись в области обратной связи в строке состояния](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [Практическое руководство. Использование области анимации в строке состояния](../misc/how-to-use-the-animation-region-of-the-status-bar.md)   
 [Практическое руководство. Программирование области конструктора в строке состояния](../Topic/How%20to:%20Program%20the%20Designer%20Region%20of%20the%20Status%20Bar.md)