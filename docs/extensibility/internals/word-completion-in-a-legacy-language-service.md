---
title: "Word завершения в языковую службу прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a4ab4bd29c753fc03787fbbadbe106d2d8862b10
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="word-completion-in-a-legacy-language-service"></a>Завершение слов в языковую службу прежних версий
Завершение слов заполняет отсутствуют символы на частично слова. Если имеется только один возможных завершения, завершения слово при вводе символ завершения. Если часть слова соответствует более одной возможности, отображается список возможных вариантов завершения. Символ завершения может быть любой символ, который не используется для идентификаторов.  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Подробнее см. в разделе [расширение редактора и языковые службы](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API, как можно быстрее. Это повысит быстродействие языковой службы и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="implementation-steps"></a>Действия по внедрению  
  
1.  Когда пользователь выбирает **завершить слово** из **IntelliSense** меню <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> отправки команды службе языка.  
  
2.  <xref:Microsoft.VisualStudio.Package.ViewFilter> Класс перехватывает команды и вызовы <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод с причиной по синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3.  <xref:Microsoft.VisualStudio.Package.Source> Вызывает класс и <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод, чтобы получить список возможных word завершений и затем отображает список слов в всплывающей подсказки с помощью <xref:Microsoft.VisualStudio.Package.CompletionSet> класса.  
  
     При наличии только одного сопоставления слова, <xref:Microsoft.VisualStudio.Package.Source> класс завершения слова.  
  
 Кроме того Если сканер возвращает значение триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> при вводе первый символ идентификатора <xref:Microsoft.VisualStudio.Package.Source> класс обнаружит это и вызывает <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод с причиной по синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>. В этом случае средство синтаксического анализа необходимо определить наличие знака выбора элемента и указать список элементов.  
  
## <a name="enabling-support-for-the-complete-word"></a>Включение поддержки для полного слова  
 Чтобы обеспечить поддержку набора завершений word `CodeSense` с именем параметра, передаваемое <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> атрибута пользователя, связанного с языкового пакета. Это задает <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.  
  
 Программу parser должен возвращать список объявлений в ответ на синтаксический анализ значение причины <xref:Microsoft.VisualStudio.Package.ParseReason>, word завершения работы.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Реализация в методе ParseSource завершение слов  
 Для завершение слов <xref:Microsoft.VisualStudio.Package.Source> класса вызывает <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> метод <xref:Microsoft.VisualStudio.Package.AuthoringScope> классе, чтобы получить список возможных word совпадений. Список необходимо реализовать в классе, который является производным от <xref:Microsoft.VisualStudio.Package.Declarations> класса. В разделе <xref:Microsoft.VisualStudio.Package.Declarations> класс подробные сведения о методах, которые необходимо реализовать.  
  
 Если список содержит только одно слово, то <xref:Microsoft.VisualStudio.Package.Source> класса автоматически вставляет слова вместо частичного слова. Если список содержит более одного слова <xref:Microsoft.VisualStudio.Package.Source> класс представляет список средств совет, из которого пользователь может выбрать подходящий вариант.  
  
 Также следует ознакомиться с примером <xref:Microsoft.VisualStudio.Package.Declarations> реализацию класса в [завершение члена в языковую службу прежних версий](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).