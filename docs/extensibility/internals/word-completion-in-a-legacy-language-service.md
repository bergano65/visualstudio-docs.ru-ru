---
title: "Завершение слов в языковую службу для прежних версий | Microsoft Docs"
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
  - "языковые службы [платформа управляемых пакетов], IntelliSense, завершение слов"
  - "Технология IntelliSense, завершение слов"
  - "Завершить слово"
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Завершение слов в языковую службу для прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Завершение слов заполняет недостающие символы на частично введенного слова. При наличии только одного возможно завершение слова завершения при вводе символ завершения. Если части слова соответствует более одной возможности, отображается список возможных вариантов завершения. Завершение может содержать любой символ, который не используется для идентификаторов.  
  
 Устаревший языковые службы реализуются как частью VSPackage, но это использование расширений MEF новый способ реализации возможностей службы языка. Для получения дополнительных см [Расширение редактора и языковые службы](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно быстрее. Это улучшает производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## Реализация действия  
  
1.  Когда пользователь выбирает **Завершить слово** из **IntelliSense** меню <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> отправляется команда языковой службы.  
  
2.  <xref:Microsoft.VisualStudio.Package.ViewFilter> Класс перехватывает команды и вызывает метод <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод синтаксического анализа причины <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3.  <xref:Microsoft.VisualStudio.Package.Source> Класс и вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод, чтобы получить список завершений возможности word и затем отображает список слов во всплывающей подсказки с помощью <xref:Microsoft.VisualStudio.Package.CompletionSet> класса.  
  
     Если имеется только один совпадающего слова <xref:Microsoft.VisualStudio.Package.Source> класс завершает слово.  
  
 Кроме того Если сканер возвращает значение триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> при вводе первого символа идентификатора <xref:Microsoft.VisualStudio.Package.Source> класс обнаруживает и вызывает <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод синтаксического анализа причины <xref:Microsoft.VisualStudio.Package.ParseReason>. В этом случае средство синтаксического анализа необходимо определить наличие знака выбора элемента и предоставить список членов.  
  
## Включение поддержки для полного слова  
 Чтобы включить поддержку набора завершений word `CodeSense` именованный параметр, передаваемый <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> атрибута пользователя, связанного с языковой пакет. Это задает <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Свойства <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.  
  
 Ваш анализатор должен возвращать список объявлений в ответ на значение синтаксического анализа причины <xref:Microsoft.VisualStudio.Package.ParseReason>, word завершения работы.  
  
## Реализация метода ParseSource завершить слово  
 Для завершения слов <xref:Microsoft.VisualStudio.Package.Source> класса вызывает <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> метод <xref:Microsoft.VisualStudio.Package.AuthoringScope> классе, чтобы получить список возможных word совпадений. Список необходимо реализовать в классе, который является производным от <xref:Microsoft.VisualStudio.Package.Declarations> класса. В разделе <xref:Microsoft.VisualStudio.Package.Declarations> класс подробные сведения о методах, которые необходимо реализовать.  
  
 Если список содержит только одно слово, а затем <xref:Microsoft.VisualStudio.Package.Source> класс автоматически вставляет слова вместо части слова. Если список содержит более одного слова <xref:Microsoft.VisualStudio.Package.Source> класс представляет список средств совет, из которого пользователь может выбрать подходящий вариант.  
  
 Также просмотрите пример <xref:Microsoft.VisualStudio.Package.Declarations> реализацию класса в [Завершение члена в языковую службу для прежних версий](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).