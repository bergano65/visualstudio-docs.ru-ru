---
title: "Краткие сведения в службе языка прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8e0fa4a65960d0324a4be19db61648be48b08349
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="quick-info-in-a-legacy-language-service"></a>Краткие сведения в службе языка прежних версий
Краткие сведения IntelliSense показывает информацию об идентификаторе в источнике, когда пользователь помещает курсор в идентификаторе и выбирает **краткие сведения** из **IntelliSense** меню или содержит мыши курсор на идентификатор. В этом случае всплывающей подсказки с информацией об идентификатор. Эти сведения обычно состоит из идентификатора типа. Когда отладчик активна, эти сведения могут включать текущее значение. Отладчик предоставляет значений выражения, пока языковая служба обрабатывает только идентификаторы.  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Подробнее см. в разделе [Пошаговое руководство: отображение кратких сведений подсказки](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API, как можно быстрее. Это повысит быстродействие языковой службы и позволяют воспользоваться преимуществами новых функций редактора.  
  
 Классы managed package framework (MPF) языка службы предоставляют полную поддержку для отображения всплывающей подсказки кратких сведений IntelliSense. Все, что нужно сделать — укажите текст для отображения и включить функцию краткие сведения.  
  
 Текст, отображаемый получается путем вызова метода <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод синтаксического анализа со значением причина синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>. Поэтому сообщает средство синтаксического анализа, чтобы получить сведения о типе (или соответствующие действия для отображения в подсказке краткие сведения) для идентификатора в расположении, указанном в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта. <xref:Microsoft.VisualStudio.Package.ParseRequest> Объект является то, что было передано <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод.  
  
 Средство синтаксического анализа необходимо проанализировать все данные до позиции в <xref:Microsoft.VisualStudio.Package.ParseRequest> объекта, чтобы определить, какие все идентификаторы. Затем средство синтаксического анализа необходимо получить идентификатор в расположении синтаксического анализа запроса. И, наконец, средство синтаксического анализа необходимо передать данные совет средства, связанные с этого идентификатора к <xref:Microsoft.VisualStudio.Package.AuthoringScope> таким образом, может возвращать текст из <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> метод.  
  
## <a name="enabling-the-quick-info-feature"></a>Включение функции краткие сведения  
 Чтобы включить функцию краткие сведения, необходимо задать `CodeSense` и `QuickInfo` именованные параметры <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Задать эти атрибуты <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> и <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> свойства.  
  
## <a name="implementing-the-quick-info-feature"></a>Реализации функции краткие сведения  
 <xref:Microsoft.VisualStudio.Package.ViewFilter> Класс обрабатывает операцию кратких сведений IntelliSense. При <xref:Microsoft.VisualStudio.Package.ViewFilter> класс получает <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> команда, класс вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод с причиной по синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> и расположение курсора во время <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> команды было отправлено. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Метод синтаксического анализа необходимо затем проанализировать вплоть до указанного расположения источника и затем анализа кода в заданном месте, чтобы определить, что для отображения в подсказке краткие сведения.  
  
 Большинство средств синтаксического анализа выполнить начального анализа всего исходного файла и сохранение результатов в дерево синтаксического анализа. Полный анализ будет проведена при <xref:Microsoft.VisualStudio.Package.ParseReason> передается <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод. Другие виды анализа затем используется для получения требуемой информации дерево синтаксического анализа.  
  
 Например, синтаксический анализ причина значение <xref:Microsoft.VisualStudio.Package.ParseReason> можно найти идентификатор в исходном расположении и выполнять поиск в дерево синтаксического анализа, чтобы получить сведения о типе. Эта информация о типах затем передается <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса и возвращается <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> метод.