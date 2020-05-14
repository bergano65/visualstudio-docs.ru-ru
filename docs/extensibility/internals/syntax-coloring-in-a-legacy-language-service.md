---
title: Раскраска Синтаксиса в службе языка наследия (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2589ec24f230287306e0ff7e802d381fb6ab18b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704762"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Цветовая маркировка синтаксиса в языковой службе прежних версий

Visual Studio использует службу окраски для идентификации элементов языка и отображения их с указанными цветами в редакторе.

## <a name="colorizer-model"></a>Модель кололизатора
 Языковая служба реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс, который затем используется редакторами. Эта реализация представляет собой отдельный объект от языковой службы, как показано на следующей иллюстрации:

 ![График SVC Colorizer](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Служба окраски синтаксиса отделена от общего механизма Visual Studio для окраски текста. Для получения дополнительной [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] информации об общем механизме, поддерживающем окраску, см. [Using Fonts and Colors](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)

 Помимо кололизатора, языковая служба может поставлять пользовательские цветные предметы, которые используются редактором, рекламируя, что он поставляет пользовательские цветные предметы. Это можно сделать, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> реализовав интерфейс на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> том же объекте, который реализует интерфейс. Он возвращает количество пользовательских цветных элементов, когда редактор вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> метод, и возвращает индивидуальный элемент, пригодный для раскрашиваемого, когда редактор вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> метод.

 Метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> возвращает объект, реализуемый интерфейсом. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> Если языковая служба поддерживает 24-битные или высокие <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> значения цвета, она <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> должна реализовать интерфейс на том же объекте, что и интерфейс.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Как VSPackage использует языковую службу Colorizer

1. VSPackage должен получить соответствующую языковую службу, которая требует, чтобы языковая служба VSPackage сделала следующее:

    1. Используйте объект, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> реализующий интерфейс, чтобы разокрасить текст.

         Текст обычно отображается с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объекта, реализующего интерфейс.

    2. Получите языковую службу, задав запрос поставщику услуг VSPackage для языкового сервиса GUID. Языковые службы идентифицируются в реестре по расширению файла.

    3. Связать языковую службу с методом, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> позвонив в ее <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> метод.

2. VSPackage теперь может получить и использовать объект colorizer следующим образом:

    > [!NOTE]
    > VSPackages, которые используют основной редактор, не должны получать объекты colorizer языковой службы явно. Как только экземпляр основного редактора получает соответствующую языковую службу, он выполняет все задачи окраски, показанные здесь.

    1. Получите объект colorizer языковой службы, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>который <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> реализует и интерфейсы, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> позвонив <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> по методу на объект языковой службы.

    2. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод для получения информации о кололизаторе для определенного диапазона текста.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>возвращает массив значений, по одному для каждого символа в пролете текста, который окрашивается. Значения индексируются в список colorable элементов, который является либо список colorable по умолчанию, поддерживаемый основным редактором, или пользовательский список цветных элементов, поддерживаемый самой языковой службой.

    3. Используйте информацию о <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> цветении, возвращенную методом, для отображения выбранного текста.

> [!NOTE]
> В дополнение к использованию цветообразной языковой службы, VSPackage также может использовать механизм окраски текста визуальной студии общего назначения. Для получения дополнительной информации об этом механизме [см.](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)

## <a name="in-this-section"></a>В этом разделе
- [Реализация цветовой маркировки синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)

 Обсуждается, как редактор получает доступ к окраске синтаксиса языковой службы и что языковая служба должна реализовать для поддержки окраски синтаксиса.

- [Практическое руководство. Использование встроенных цветных элементов](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Демонстрирует, как использовать встроенные цветные элементы из языковой службы.

- [Настраиваемые цветные элементы](../../extensibility/internals/custom-colorable-items.md)

 Обсуждает, как реализовать пользовательские цветные элементы.
