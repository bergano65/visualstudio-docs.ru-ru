---
title: Наследие Языковая служба Основы (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 501bccf755293e86e8a9dc23fce125a10c882376
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707426"
---
# <a name="legacy-language-service-essentials"></a>Основные компоненты языковой службы прежних версий
Необходимо предоставить языковую службу для интеграции языка программирования в Visual Studio. В этой теме разъясняются функции, доступные в устаревших языковых службах.

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше о новом способе реализации языковой [службы,](../../extensibility/editor-and-language-service-extensions.md)см.

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

 Устаревшие языковые службы предоставляют следующие функции:

|Компонент|Описание|
|-------------|-----------------|
|Цветовая подсветка синтаксиса|Вызывает представление редактора для отображения различных цветов и стилей шрифтов для различных элементов языка. Эта дифференциация может упростить чтение и ред., отодвинет файлы.<br /><br /> Для получения общей [информации см.](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)<br /><br /> Для получения информации об этой функции в структуре управляемого пакета (MPF) см. [Syntax Colorizing в языковой службе Legacy.](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)|
|Завершение операторов|Завершает выписку или ключевое слово, которое пользователь начал вводить. Завершение выполнения оператора помогает пользователям вводить сложные операторы более легко, с меньшим ввоза и меньше шансов на ошибку.<br /><br /> Для получения общей [Statement Completion in a Legacy Language Service](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)информации см.<br /><br /> Для получения информации об этой [Word Completion in a Legacy Language Service](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)функции в MPF см.|
|Соответствие скобок|Основные символы, такие как скобки. Когда пользователь вводит закрывающий символ, такой как «я», соответствие скобки выделяет соответствующий символ открытия, например « Когда существует несколько уровней прилагающих к ней символов, эта функция помогает пользователям подтвердить, что прилагающие символы сопряжены правильно.<br /><br /> Для получения информации об этой [Brace Matching in a Legacy Language Service](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)функции в MPF см.|
|Параметр информационные инструменты|Отображает список возможных подписей для перегруженного метода, который пользователь в настоящее время печатает.<br /><br /> Для получения общей информации [см.](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)<br /><br /> Для получения информации об этой функции в MPF [см.](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)|
|Маркеры ошибок|Отображает волнистый красный подчеркнуть, также известный как squiggly, под текстом, который синтаксически неправильно. Маркеры ошибок обычно используются для информирования пользователей о неправильно написанных ключевых словах, незакрытых скобках, недействительных символах и аналогичных ошибках.<br /><br /> В классах MPF маркеры ошибок обрабатываются автоматически <xref:Microsoft.VisualStudio.Package.AuthoringSink> в методе <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> класса.|

 Многие из этих функций требуют языкового сервиса для разбора исходного кода. Часто можно повторно использовать код токенизации и разбора для компилятора или переводчика.

 Следующие функции связаны с поддержкой языков программирования, но не являются частью языковых служб:

| Компонент | Описание |
|-----------------------| - |
| Оценки экспрессии | [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Поддерживает отладку, валидируя точки разрыва и предоставляя список выражений, которые будут отображаться в окне отладки **Autos.**<br /><br /> Для получения дополнительной информации обратитесь [в службу поддержки языковой службы для debugging](../../extensibility/internals/language-service-support-for-debugging.md). |
| Инструменты просмотра символов | Поддерживает **объектный браузер,** **просмотр классов,** **поиск браузера**и **поиск результатов символов.** |
