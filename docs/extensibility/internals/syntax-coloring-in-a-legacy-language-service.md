---
title: Выделение синтаксиса в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa3dcadfc7774766c0e76617ce133d2c30ba2aa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186322"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Цветовая маркировка синтаксиса в языковой службе прежних версий

Visual Studio использует службу цветового выделения для распознавания элементов языка и отображения их с указанными цветами в редакторе.

## <a name="colorizer-model"></a>Модель тонирования
 Языковая служба реализует интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>, который затем используется редакторами. Эта реализация является отдельным объектом из языковой службы, как показано на следующем рисунке:

 ![График SVC Colorizer](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Служба цветового выделения синтаксиса отличается от общего механизма Visual Studio для выделения цветом текста. Дополнительные сведения об общем механизме [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], поддерживающем окраска, см. в разделе [Использование шрифтов и цветов](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

 Помимо «тонирования», языковая служба может предоставлять настраиваемые цветовые элементы, используемые редактором, составлять объявления о том, что он предоставляет настраиваемые цветные элементы. Это можно сделать, реализовав интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> для того же объекта, который реализует интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>. Он возвращает число настраиваемых цветовых элементов, когда редактор вызывает метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>, и возвращает отдельный настраиваемый цветовой элемент, когда редактор вызывает метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.

 Метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> возвращает объект, реализующий интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>. Если языковая служба поддерживает 24-разрядные или высокие значения цвета, она должна реализовывать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> для того же объекта, что и интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Как VSPackage использует цветовой цвет языковой службы

1. Пакет VSPackage должен получить соответствующую языковую службу, которая требует пакета VSPackage языковой службы, чтобы выполнить следующие действия:

    1. Используйте объект, реализующий интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>, чтобы получить текст для выделения цветом.

         Текст обычно отображается с помощью объекта, реализующего интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

    2. Получите языковую службу, запросив поставщика служб VSPackage для идентификатора GUID языковой службы. Языковые службы определяются в реестре по расширению файла.

    3. Свяжите языковую службу с <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>, вызвав метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>.

2. Пакет VSPackage теперь может получить и использовать объект «окраска» следующим образом:

    > [!NOTE]
    > Пакеты VSPackage, использующие основной редактор, не должны явным образом получать объекты цветовой службы языка. Как только экземпляр базового редактора получает соответствующую языковую службу, он выполняет все задачи выделения цветом, показанные здесь.

    1. Получите объект языковой поддержки, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>и интерфейсы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>, вызвав метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> для объекта <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> языковой службы.

    2. Вызовите метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>, чтобы получить сведения о параметрах выделения цветом для определенного фрагмента текста.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> возвращает массив значений, по одному для каждого символа в цветовом диапазоне текста. Значения — это индексы в списке элементов с цветовым списком, который является либо списком элементов по умолчанию, поддерживаемым основным редактором, либо настраиваемым списком элементов, поддерживаемым самой языковой службой.

    3. Используйте сведения о цветовой отсчете, возвращаемые методом <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> для вывода выбранного текста.

> [!NOTE]
> Помимо использования цветового интерфейса языковой службы, VSPackage также может использовать механизм выделения цветом текста общего назначения Visual Studio. Дополнительные сведения об этом механизме см. [в разделе Использование шрифтов и цветов](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="in-this-section"></a>Содержание
- [Реализация цветовой маркировки синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)

 Описывает, как редактор обращается к цветовой маркировке синтаксиса языковой службы и какую языковую службу необходимо реализовать для поддержки цветового выделения синтаксиса.

- [Практическое руководство. Использование встроенных цветных элементов](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Демонстрирует использование встроенных цветовых элементов из языковой службы.

- [Настраиваемые цветные элементы](../../extensibility/internals/custom-colorable-items.md)

 Обсуждается реализация пользовательских цветовых элементов.