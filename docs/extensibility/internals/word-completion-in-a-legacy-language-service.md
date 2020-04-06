---
title: Слово Завершение в Наследие Языковая служба (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 948751cde5b6b710d911a30ca26a61e5411bba4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703166"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Завершение машинных слов в языковой службе прежних версий
Завершение слова заполняет недостающие символы на частично набранном слове. Если есть только одно возможное завершение, слово завершается при входе в символ завершения. Если частичное слово совпадает с более чем одной возможностью, отображается список возможных завершений. Символом завершения может быть любой символ, который не используется для идентификаторов.

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше, смотрите [Расширение редактора и языковых служб](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

## <a name="implementation-steps"></a>Шаги реализации

1. Когда пользователь выбирает **Полное Слово** из меню **IntelliSense,** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> команда отправляется в языковую службу.

2. Класс <xref:Microsoft.VisualStudio.Package.ViewFilter> ловит команду и <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> вызывает метод с причиной <xref:Microsoft.VisualStudio.Package.ParseReason>разбора .

3. Затем <xref:Microsoft.VisualStudio.Package.Source> класс вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод, чтобы получить список возможных завершений слов, а <xref:Microsoft.VisualStudio.Package.CompletionSet> затем отображает слова в списке наконечников инструментов с помощью класса.

    Если есть только одно соответствующее <xref:Microsoft.VisualStudio.Package.Source> слово, класс завершает слово.

   Кроме того, если сканер возвращает <xref:Microsoft.VisualStudio.Package.TokenTriggers> значение триггера при набранном первом <xref:Microsoft.VisualStudio.Package.Source> символе идентификатора, класс обнаруживает это и вызывает <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> метод с причиной разбора <xref:Microsoft.VisualStudio.Package.ParseReason>. В этом случае парсер должен обнаружить наличие символа выбора участника и предоставить список членов.

## <a name="enabling-support-for-the-complete-word"></a>Включение поддержки полного слова
 Для поддержки набора завершения `CodeSense` слова указанный <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> параметр передается атрибуту пользователя, связанному с пакетом языка. Это устанавливает <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> на класс.

 Ваш парсер должен вернуть список деклараций в ответ <xref:Microsoft.VisualStudio.Package.ParseReason>на значение причины разбора, для завершения слова для работы.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Реализация Полного слова в методе ParseSource
 Для завершения слова <xref:Microsoft.VisualStudio.Package.Source> класс <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> вызывает метод <xref:Microsoft.VisualStudio.Package.AuthoringScope> в классе, чтобы получить список возможных совпадений слов. Необходимо реализовать список в классе, который <xref:Microsoft.VisualStudio.Package.Declarations> происходит из класса. Просмотрите <xref:Microsoft.VisualStudio.Package.Declarations> класс для получения подробной информации о методах, которые необходимо реализовать.

 Если список содержит только одно <xref:Microsoft.VisualStudio.Package.Source> слово, то класс автоматически вставляет это слово вместо частичного слова. Если список содержит более одного <xref:Microsoft.VisualStudio.Package.Source> слова, класс представляет список наконечников инструментов, из которого пользователь может выбрать подходящий выбор.

 Также посмотрите на <xref:Microsoft.VisualStudio.Package.Declarations> пример реализации класса в [Службе обучения в Языковой службе Legacy.](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)
