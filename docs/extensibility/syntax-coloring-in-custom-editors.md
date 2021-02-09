---
title: Выделение синтаксиса в пользовательских редакторах | Документация Майкрософт
description: Сведения о цветовом синтаксисе в пользовательских редакторах пакета SDK для среды Visual Studio, в которых отображаются указанные цвета для данного представления документа.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bedfdffd91c4e15de556609a030f7e0238a7e7d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880714"
---
# <a name="syntax-coloring-in-custom-editors"></a>Цветовая маркировка синтаксиса в специализированных редакторах
Редакторы пакетов SDK для среды Visual Studio, включая основной редактор, используют языковые службы для поиска определенных синтаксических элементов и отображают их с указанными цветами для данного представления документа.

## <a name="colorization-requirements"></a>Требования к цветам
 Все редакторы, реализующие окраска языковой службы, должны:

1. Используйте объект, реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> для управления цветом текста, и объект, реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для предоставления представления текста в виде документа.

2. Получите интерфейс для конкретной языковой службы, запрашивая поставщика услуг VSPackage, используя идентифицирующий идентификатор GUID службы языков.

3. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> метод объекта, реализующего <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> . Этот метод связывает языковую службу с <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> реализацией, которую пакет VSPackage использует для управления цветом текста.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Использование основного редактора для цветового выделения языковой службы
 Когда экземпляр базового редактора получает языковую службу с аппаратным фильтром, синтаксический анализ и отрисовка текста с помощью цветового средства языковой службы происходит автоматически, без необходимости дальнейшего вмешательства с вашей стороны.

 Прозрачная среда IDE:

- Вызывает метод выделения цветом для синтаксического анализа и анализа текста при его добавлении или изменении в реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .

- Гарантирует, что отображение, предоставленное представлением документа, предоставленным при <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> реализации, обновляется и перерисовывается с использованием сведений, возвращаемых параметром тонирования.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Небазовое использование редактора для цветового выделения языковой службы
 Экземпляры редактора, не являющиеся ядрами, также могут использовать службу раскраски синтаксиса языковой службы, но они должны явно получить и применить цветовой режим службы, а также перекрасить свои представления документов.

 Для этого неядерный редактор должен:

1. Получите объект языковой службы языка (который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> ). Пакет VSPackage делает это путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> метода в интерфейсе языковой службы.

2. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод, чтобы запросить выделение цветом определенного фрагмента текста.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Метод возвращает массив значений, по одному для каждой буквы в цветовом диапазоне текста. Он также определяет текстовый диапазон как определенный тип цветового элемента, например комментарий, ключевое слово или тип данных.

3. Используйте сведения о цветовой отсчете, возвращаемые функцией, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> для перерисовки и вывода текста.

> [!NOTE]
> Помимо использования средства выбора цветов языковой службы, VSPackage может использовать механизм цветового выделения текста пакета SDK для среды Visual Studio общего назначения. Дополнительные сведения об этом механизме см. в разделе [Использование шрифтов и цветов](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>См. также раздел

- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Реализация цветовой маркировки синтаксиса](../extensibility/internals/implementing-syntax-coloring.md)
- [Практическое руководство. Использование встроенных цветных элементов](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Настраиваемые цветные элементы](../extensibility/internals/custom-colorable-items.md)