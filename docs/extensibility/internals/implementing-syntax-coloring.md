---
title: Реализация цветовой маркировки синтаксиса | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e82246a750c26881a055e372baa7d5eb0386952
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596092"
---
# <a name="implementing-syntax-coloring"></a>Реализация цветовой маркировки синтаксиса
Если служба языка предоставляет цветовое выделение синтаксиса, средство синтаксического анализа преобразует строку текста в массив цветных элементов и возвращает типы маркеров, соответствующий эти цветных элементов. Средство синтаксического анализа должна возвращать маркера типов, входящих в список цветных элементов. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отображает каждого цветного элемента в окне кода, в соответствии с атрибуты, присвоенные этим объектом палитры к соответствующему типу маркера.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Указывает интерфейс средства синтаксического анализа, и средство синтаксического анализа реализации полностью зависит от вас. Тем не менее средство синтаксического анализа реализацию по умолчанию предоставляется в проекте языковой пакет Visual Studio. Для управляемого кода managed package framework (MPF) обеспечивает полную поддержку для выделения текста цветом.

 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Чтобы узнать больше о новый способ реализовать раскраску синтаксических конструкций, см. в разделе [Пошаговое руководство: Выделение текста](../../extensibility/walkthrough-highlighting-text.md).

> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Действия, выполняемые с помощью редактора для выделения текста цветом

1.  Редактор получает палитру, путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> объекта.

2.  Вызывает редактор <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> метод, чтобы определить необходимость палитры состояние каждой строки, чтобы удовлетворять вне палитры.

3.  Если палитре требуется состояние, которое должно удовлетворять вне палитры, вызывает редактор <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> метод для получения состояния первой строки.

4.  Для каждой строки в буфере, вызывает редактор <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод, который выполняет следующие действия:

    1.  Строка текста, передается сканер для преобразования текста в токены. Каждый маркер указывает текст токена и тип маркера.

    2.  Тип токена преобразуется в индекс в список цветных элементов.

    3.  Сведения о токене используется для заполнения массива таким образом, что каждый элемент в массиве соответствует символа в строке. Значения, хранящиеся в массиве являются индексы в список цветных элементов.

    4.  Для каждой строки, возвращается состояние в конце строки.

5.  Если палитре требуется сохранения состояния, в редакторе кэширует состояние для этой строки.

6.  Редактор отображает строку текста, используя сведения, полученные из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод. Для этого необходимо выполнить следующие действия:

    1.  Для каждого символа в строке получите индекс цветного элемента.

    2.  Если с помощью цветных элементов по умолчанию, доступ к редактора цветных элементов списка.

    3.  В противном случае вызовите языковой службы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> метод, чтобы получить цветного элемента.

    4.  Используйте сведения в цветного элемента для отображения текста на экране.

## <a name="managed-package-framework-colorizer"></a>Managed Package Framework палитры
 Managed package framework (MPF) предоставляет все классы, которые необходимы для реализации палитры. Класс службы языка должен наследовать <xref:Microsoft.VisualStudio.Package.LanguageService> класса и реализовать требуемые методы. Необходимо ввести сканера и средство синтаксического анализа путем реализации <xref:Microsoft.VisualStudio.Package.IScanner> интерфейс и возвратить экземпляр этого интерфейса из <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метод (один из методов, которые должны быть реализованы в <xref:Microsoft.VisualStudio.Package.LanguageService> класса). Дополнительные сведения см. в разделе [цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="see-also"></a>См. также
- [Практическое руководство. Использование встроенных цветных элементов](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Настраиваемые цветные элементы](../../extensibility/internals/custom-colorable-items.md)
- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)