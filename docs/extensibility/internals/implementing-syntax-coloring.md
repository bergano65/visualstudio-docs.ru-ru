---
title: Применение цветового выделения синтаксиса | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cab338e253cca8c7f8457752980e7f3624317d9c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727028"
---
# <a name="implementing-syntax-coloring"></a>Реализация цветовой маркировки синтаксиса
Если языковая служба предоставляет цветовую раскраску синтаксиса, средство синтаксического анализа преобразует строку текста в массив цветных элементов и возвращает типы токенов, соответствующие этим цветовым элементам. Средство синтаксического анализа должно возвращать типы токенов, принадлежащие списку цветовых элементов. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отображает каждый цветовой элемент в окне кода в соответствии с атрибутами, назначенными объектом тонирования, соответствующему типу токена.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] не указывает интерфейс средства синтаксического анализа, а реализация средства синтаксического анализа полностью подоходила вам. Однако реализация средства синтаксического анализа по умолчанию предоставляется в проекте языкового пакета Visual Studio. Для управляемого кода платформа управляемого пакета (MPF) обеспечивает полную поддержку выделения цветом текста.

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения о новом способе реализации цветового выделения синтаксиса см. в разделе [Пошаговое руководство. выделение текста](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Шаги, за которыми следует редактор для выделения цветом текста

1. Редактор получает цветовой элемент, вызывая метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> для объекта <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>.

2. Редактор вызывает метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>, чтобы определить, требуется ли для каждого из этих строк состояние, которое должно поддерживаться за пределами тонирования.

3. Если для параметра тонирования требуется поддерживать состояние вне области выделения, редактор вызывает метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>, чтобы получить состояние первой строки.

4. Для каждой строки в буфере редактор вызывает метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>, который выполняет следующие действия:

    1. Строка текста передается сканеру для преобразования текста в маркеры. Каждый токен задает текст маркера и тип токена.

    2. Тип токена преобразуется в индекс в список цветовых элементов.

    3. Сведения о токене используются для заполнения массива таким, чтобы каждый элемент массива соответствовал символу в строке. Значения, хранящиеся в массиве, являются индексами в списке цветовых элементов.

    4. Состояние в конце строки возвращается для каждой строки.

5. Если для этого режима требуется поддерживать состояние, редактор кэширует состояние этой строки.

6. Редактор отображает строку текста, используя сведения, возвращаемые методом <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>. Для этого необходимо выполнить следующие действия:

    1. Для каждого символа в строке Возвращает цветовой индекс элемента.

    2. При использовании цветовых элементов по умолчанию можно получить доступ к списку цветовых элементов редактора.

    3. В противном случае вызовите метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> языковой службы для получения цветового элемента.

    4. Используйте сведения в элементе с цветовым цветом, чтобы подготовить текст к отображению.

## <a name="managed-package-framework-colorizer"></a>Цветовой пакет для платформы управляемых пакетов
 Платформа управляемого пакета (MPF) предоставляет все классы, необходимые для реализации выделения цветом. Класс языковой службы должен наследовать класс <xref:Microsoft.VisualStudio.Package.LanguageService> и реализовать необходимые методы. Необходимо предоставить сканер и средство синтаксического анализа, реализовав интерфейс <xref:Microsoft.VisualStudio.Package.IScanner>, и вернуть экземпляр этого интерфейса из метода <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> (один из методов, которые должны быть реализованы в классе <xref:Microsoft.VisualStudio.Package.LanguageService>). Дополнительные сведения см. [в разделе тонирование синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>См. также
- [Практическое руководство. Использование встроенных цветных элементов](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Настраиваемые цветные элементы](../../extensibility/internals/custom-colorable-items.md)
- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)