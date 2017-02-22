---
title: "Практическое руководство: поддержка структурирование в языковую службу для прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] свернуть в определения команд"
  - "языковые службы, поддерживающие свернуть в определения команд"
  - "Скрытый текст, свернуть в определения команд"
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: поддержка структурирование в языковую службу для прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Чтобы развернуть или свернуть различных областей текста используется структурирование. Используемый способ структурирования определены по\-разному в разных языках. Для получения дополнительной информации см. [Структура](../../ide/outlining.md).  
  
 Устаревший языковые службы реализуются как частью VSPackage, но это использование расширений MEF новый способ реализации возможностей службы языка. Чтобы узнать больше о новый способ реализации структуры, в разделе [Пошаговое руководство: структурирование](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно быстрее. Это улучшает производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
 Ниже показано, как для поддержки этой команды для службы языка.  
  
### Для поддержки структурирование  
  
1.  Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> на объект языковой службы.  
  
2.  Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> текущего структурирования объекта сеанса, чтобы добавить новые области структуры.  
  
## Отказоустойчивость  
 При выборе пользователем **Свернуть в определения** на **Структура** меню, вызывает IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> языковой службы.  
  
 При вызове этот метод передает IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> указатель \(указатель на буфер текста\) и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> \(указатель на текущий сеанс структурирования\).  
  
 Можно вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> метод для нескольких областей структуры путем указания в этих регионах `rgOutlnReg` параметр.`rgOutlnReg` Параметр <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> структуры. Этот процесс позволяет задавать различные характеристики скрытые области, например развернут или свернут определенного региона.  
  
> [!NOTE]
>  Будьте внимательны скрытие символы новой строки. Скрытый текст должен следовать от начала первой строки к последней символ последней строки в раздел, оставляя видимыми последним символом новой строки.  
  
## См. также  
 [Практическое руководство: обеспечивает поддержку скрытого текста в языковую службу для прежних версий](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Практическое руководство: обеспечивают расширенную поддержку создания структуры в языковую службу для прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)