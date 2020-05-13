---
title: Реализация раскраски Синтаксиса (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83ce66dd6a31e3ef852feb91e2ba304e6688a723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707647"
---
# <a name="implementing-syntax-coloring"></a>Реализация цветовой маркировки синтаксиса
Когда языковая служба предоставляет синтаксисную окраску, парсер преобразует строку текста в массив цветных элементов и возвращает типы маркеров, соответствующие этим цветовым элементам. Парсер должен возвращать типы токенов, которые относятся к списку цветных элементов. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]отображает каждый цветной элемент в окне кода в соответствии с атрибутами, назначенными объектом colorizer соответствующему типу маркера.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]не указывает интерфейс парсера, и реализация парсера полностью за вами. Тем не менее, реализация парсера по умолчанию предусмотрена в проекте Visual Studio Language Package. Для управляемого кода платформа управляемого пакета (MPF) обеспечивает полную поддержку для окраски текста.

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше о новом способе реализации окраски синтаксиса, смотрите [Пошаговая: Выделение текста](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Шаги, за которыми следует редактор, чтобы окрасить текст

1. Редактор получает кололизатор, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> вызывая <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> метод на объекте.

2. Редактор вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> метод, чтобы определить, нужно ли окрасителю состояние каждой строки для поддержания вне цветора.

3. Если окраран требует, чтобы состояние сохранялось вне <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> цветора, редактор называет метод, чтобы получить состояние первой строки.

4. Для каждой строки в буфере редактор называет <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод, выполняемый следующими шагами:

    1. Строка текста передается сканеру для преобразования текста в токены. Каждый маркер определяет текст маркера и тип маркера.

    2. Тип маркера преобразуется в индекс в список цветных элементов.

    3. Информация токенов используется для заполнения массива таким образом, чтобы каждый элемент массива соответствовал символу в строке. Значения, хранящиеся в массиве, являются индексами в список цветных элементов.

    4. Состояние в конце строки возвращается для каждой строки.

5. Если окрашитель требует сохранения состояния, редактор кэширует состояние для этой строки.

6. Редактор предоставляет строку текста, используя информацию, возвращенную из метода. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Для этого необходимо выполнить следующие действия:

    1. Для каждого символа в строке, получить цветной индекс элемента.

    2. При использовании цветных элементов по умолчанию получите доступ к списку цветных элементов редактора.

    3. В противном случае позвоните <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> в метод языковой службы, чтобы получить окрабоспособный элемент.

    4. Используйте информацию в цветном элементе, чтобы сделать текст на дисплее.

## <a name="managed-package-framework-colorizer"></a>Управляемый пакет рамочный колорит
 Платформа управляемого пакета (MPF) предоставляет все классы, необходимые для реализации расцвета. Ваш класс языковых <xref:Microsoft.VisualStudio.Package.LanguageService> служб должен наследовать класс и реализовать необходимые методы. Необходимо предоставить сканер и парсер, <xref:Microsoft.VisualStudio.Package.IScanner> реализовав интерфейс, и <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> вернуть экземпляр этого интерфейса из метода <xref:Microsoft.VisualStudio.Package.LanguageService> (один из методов, которые должны быть реализованы в классе). Для получения дополнительной информации смотрите [Syntax Colorizing в службе языка Legacy.](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

## <a name="see-also"></a>См. также
- [Практическое руководство. Использование встроенных цветных элементов](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Настраиваемые цветные элементы](../../extensibility/internals/custom-colorable-items.md)
- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
