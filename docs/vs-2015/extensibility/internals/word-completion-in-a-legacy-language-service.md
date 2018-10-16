---
title: Word завершения в языковой службе прежних версий | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 591967bd9ac61b611b1b062a006a5069fc94d114
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285302"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Завершение машинных слов в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Завершение слов заполняет недостающие символы на частично введенного слова. Если имеется только один из возможных завершения, слово завершения при вводе знака завершения. Если частичное соответствует более одной возможности, отображается список возможных завершений. Символ завершения может быть любой символ, который не используется для идентификаторов.  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [расширение редактора и языковых служб](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="implementation-steps"></a>Действия по внедрению  
  
1.  Когда пользователь выбирает **завершение слов** из **IntelliSense** меню <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> команда отправляется службе языка.  
  
2.  <xref:Microsoft.VisualStudio.Package.ViewFilter> Класс перехватывает команду, а вызовы <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод с причиной по синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3.  <xref:Microsoft.VisualStudio.Package.Source> Класс и вызовы <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод, чтобы получить список возможных word завершений и выводится список слов во всплывающей подсказки с помощью <xref:Microsoft.VisualStudio.Package.CompletionSet> класса.  
  
     Если имеется только один совпадающего слова <xref:Microsoft.VisualStudio.Package.Source> класс завершения слова.  
  
 Кроме того Если средство проверки возвращает значение триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> при вводе первого символа идентификатора <xref:Microsoft.VisualStudio.Package.Source> класс обнаружит это и вызывает <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод с причиной по синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>. В этом случае средство синтаксического анализа необходимо определить наличие знака выбора элемента и предоставить список элементов.  
  
## <a name="enabling-support-for-the-complete-word"></a>Включение поддержки для завершения слова  
 Чтобы включить поддержку набора завершений word `CodeSense` именованный параметр, передаваемый <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> атрибут пользователя, связанные с данным пакетом языка. Этот параметр задает <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.  
  
 Ваши средства синтаксического анализа должен возвращать список объявлений в ответ на синтаксический анализ значение причины <xref:Microsoft.VisualStudio.Package.ParseReason>, для завершения слова для работы.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Реализация завершение слов в методе ParseSource  
 Для завершения слова <xref:Microsoft.VisualStudio.Package.Source> вызываемый классом <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> метод <xref:Microsoft.VisualStudio.Package.AuthoringScope> классе, чтобы получить список возможных word совпадений. Необходимо реализовать в классе, который является производным от списка <xref:Microsoft.VisualStudio.Package.Declarations> класса. См. в разделе <xref:Microsoft.VisualStudio.Package.Declarations> класс Дополнительные сведения о методах, необходимо реализовать.  
  
 Если список содержит только одно слово, а затем <xref:Microsoft.VisualStudio.Package.Source> класс автоматически вставляет это слово вместо частичного слова. Если список содержит более одного слова <xref:Microsoft.VisualStudio.Package.Source> класс предоставляет список средств tip, из которого пользователь может выбрать подходящий вариант.  
  
 Также рассмотрим пример <xref:Microsoft.VisualStudio.Package.Declarations> реализацию класса в [завершение участников в языковой службе прежних версий](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).

