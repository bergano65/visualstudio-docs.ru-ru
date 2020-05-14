---
title: Быстрая информация в устаревшей языковой службе (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d070c607313b406f036a5b6f071eaa371070408
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705942"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Краткие сведения в языковой службе прежних версий
IntelliSense Быстрая информация показывает информацию об идентификаторе в источнике, когда пользователь либо помещает caret в идентификатор и выбирает **Быструю информацию** из меню **IntelliSense** или держит курсор мыши над идентификатором. Это приводит к тому, что наконечник инструмента появляется с информацией об идентификаторе. Эта информация обычно состоит из типа идентификатора. Когда движок отладки активен, эта информация может включать текущее значение. Отладка двигателя поставляет значения выражения, в то время как языковая служба обрабатывает только идентификаторы.

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше, [см.](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

 Классы языковых услуг управляемого пакета (MPF) обеспечивают полную поддержку для отображения наконечника инструмента IntelliSense Быстрая информация. Все, что вам нужно сделать, это поставить текст для отображения и включить функцию быстрой информации.

 Текст, который будет отображаться, получен <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> путем вызова метода парсер <xref:Microsoft.VisualStudio.Package.ParseReason>с разбором значение причины . Эта причина говорит parser для того чтобы получить информацию типа (или все, что соотвествующее <xref:Microsoft.VisualStudio.Package.ParseRequest> быть отображено в подсказке инструмента быстроinfo) для идентификатора на положении, указанном в объекте. Объект <xref:Microsoft.VisualStudio.Package.ParseRequest> — это то, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> что было передано методу.

 Парсер должен разобрать все до положения объекта, <xref:Microsoft.VisualStudio.Package.ParseRequest> чтобы определить типы всех идентификаторов. Затем парсер должен получить идентификатор в месте запроса. Наконец, парсер должен передать объекту данные наконечника инструмента, связанные с этим идентификатором, чтобы <xref:Microsoft.VisualStudio.Package.AuthoringScope> объект мог вернуть текст из метода. <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A>

## <a name="enabling-the-quick-info-feature"></a>Включение функции быстрой информации
 Для включения функции «Быстрая `CodeSense` информация» необходимо установить и `QuickInfo` назвать <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>параметры. Эти атрибуты <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> устанавливают <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> свойства и свойства.

## <a name="implementing-the-quick-info-feature"></a>Реализация функции «Быстрая информация»
 Класс <xref:Microsoft.VisualStudio.Package.ViewFilter> обрабатывает операцию IntelliSense Быстрая информация. Когда <xref:Microsoft.VisualStudio.Package.ViewFilter> класс получает <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> команду, класс <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> вызывает метод с причиной <xref:Microsoft.VisualStudio.Package.ParseReason> разбора и расположением caret <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> во время отправки команды. Затем <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> парсер метода должен разогнать источник до данного местоположения, а затем разобрать идентификатор в данном месте, чтобы определить, что отобразить в наконечнике инструмента «Быстрая информация».

 Большинство разборников делают первоначальный разбор всего исходного файла и хранят результаты в дереве разбора. Полный разбор осуществляется при <xref:Microsoft.VisualStudio.Package.ParseReason> перегоне к методу. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Другие виды разбора могут затем использовать дерево разбора для получения нужной информации.

 Например, значение причины разбора <xref:Microsoft.VisualStudio.Package.ParseReason> может найти идентификатор в исходном месте и посмотреть его в дереве разбора для получения информации о типе. Информация этого типа затем <xref:Microsoft.VisualStudio.Package.AuthoringScope> передается классу <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> и возвращается методом.
