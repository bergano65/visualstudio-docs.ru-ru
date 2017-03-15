---
title: "Краткие сведения в языковую службу для прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Краткие сведения, поддержке в языковые службы [платформа управляемых пакетов]"
  - "Технология IntelliSense, краткие сведения"
  - "языковые службы [платформа управляемых пакетов] кратких сведений IntelliSense"
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Краткие сведения в языковую службу для прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Краткие сведения IntelliSense показывает информацию об идентификаторе в источнике, когда пользователь помещает курсор в идентификаторах и выбирает **Краткие сведения** из **IntelliSense** меню или содержит курсор мыши над ним. В результате всплывающей подсказки с информацией об идентификатор. Эти сведения обычно состоит из идентификатора типа. Когда отладчик активен, эта информация может включать текущее значение. Отладчик предоставляет значения выражения, пока языковая служба обрабатывает только идентификаторы.  
  
 Устаревший языковые службы реализуются как частью VSPackage, но это использование расширений MEF новый способ реализации возможностей службы языка. Для получения дополнительных см [Пошаговое руководство: Отображение кратких сведений подсказки](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно быстрее. Это улучшает производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
 Управляемых пакетов framework \(MPF\) языковой службы классы обеспечивают полную поддержку для отображения всплывающей подсказки IntelliSense Quick Info. Нужно всего лишь указать текст, который будет отображаться и включить функцию краткие сведения.  
  
 Текст, отображаемый получается путем вызова метода <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод синтаксического анализа со значением причина синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>. Поэтому сообщает средство синтаксического анализа, чтобы получить сведения о типе \(или соответствующие действия для отображения в подсказке краткие сведения\) для идентификатора в расположении, указанном в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта.<xref:Microsoft.VisualStudio.Package.ParseRequest> Объект является то, что было передано <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод.  
  
 Средство синтаксического анализа необходимо проанализировать все до позиции в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта, чтобы определить, какие идентификаторы. Затем средство синтаксического анализа необходимо получить идентификатор запроса на месте синтаксического анализа. Наконец, средство синтаксического анализа необходимо передать данные tip средство, связанный с этим идентификатором для <xref:Microsoft.VisualStudio.Package.AuthoringScope> таким образом, чтобы этот объект можно вернуть текст из <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> метод.  
  
## Включение функции кратких сведений  
 Чтобы включить функцию краткие сведения, необходимо задать `CodeSense` и `QuickInfo` Параметры с именем <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Эти атрибуты заданы <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> и <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> Свойства.  
  
## Реализация функции кратких сведений  
 <xref:Microsoft.VisualStudio.Package.ViewFilter> Класс обрабатывает операции кратких сведений IntelliSense. При <xref:Microsoft.VisualStudio.Package.ViewFilter> получает класс <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> команды, класс вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод parse причину <xref:Microsoft.VisualStudio.Package.ParseReason> и положением курсора во время <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> команда была отправлена.<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Метод синтаксического анализа необходимо затем проанализировать источника вплоть до указанного расположения и затем анализа кода в заданном месте, чтобы определить, что для отображения всплывающей подсказки Quick Info.  
  
 Большинство анализаторы сделать начального анализа всего исходного файла и сохранение результатов в дерево синтаксического анализа. Полный анализ выполняется при <xref:Microsoft.VisualStudio.Package.ParseReason> передается <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод. Другие виды анализа затем можно использовать дерево синтаксического анализа для получения требуемой информации.  
  
 Например, синтаксический анализ причин значение <xref:Microsoft.VisualStudio.Package.ParseReason> можно найти идентификатор в исходном расположении и выполнять поиск в дереве синтаксического анализа, чтобы получить сведения о типе. Сведения о типе затем передается <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса и возвращается <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> метод.