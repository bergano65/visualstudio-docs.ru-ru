---
title: Раскраска Синтаксиса в пользовательских редакторах (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6296c8451684a121ac42dbde6619c0ebbb421908
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699337"
---
# <a name="syntax-coloring-in-custom-editors"></a>Цветовая маркировка синтаксиса в специализированных редакторах
Редакторы Visual Studio Environment SDK, включая основного редактора, используют языковые службы для определения конкретных синтаксисных элементов и отображения их с указанными цветами для данного представления документа.

## <a name="colorization-requirements"></a>Требования к цветизации
 Все редакторы, реализующие кололизатор языковой службы, должны:

1. Используйте объект, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> реализующий для управления цветом <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> текста, и объект, реализующий, для представления документа.

2. Получите интерфейс с определенной языковой службой, задав запрос поставщику услуг VSPackage, используя языковую службу, идентифицирующую GUID.

3. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> метод реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>объекта. Этот метод связывает языковую <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> службу с реализацией, которую VSPackage использует для управления текстом, который должен быть раскрашеным.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Основной редактор Использование Colorizer языковой службы
 Когда языковая служба с кололизатором получена экземпляром основного редактора, разбор и визуализация текста кололизатором языковой службы происходит автоматически, не требуя дальнейшего вмешательства с вашей стороны.

 IDE прозрачно:

- Вызывает окраситель по мере необходимости для анализа и анализа текста <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>при его добавлении или изменении в реализации.

- Гарантирует, что дисплей, представленный представлением <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> документа, представленным реализацией, обновляется и перекрашивается с использованием информации, возвращенной окрашителем.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Неосновной редактор Использование Colorizer языковой службы
 Непрофильные экземпляры редактора также могут использовать службу синтаксиса языковой службы, но они должны явно извлекать и применять колоризатор службы и перекрашивать представления своих документов самостоятельно.

 Для этого непрофильный редактор должен:

1. Получить объект colorizer языковой службы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> (который реализует и). <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> VSPackage делает это, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> вызывая метод на интерфейсе языковой службы.

2. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод, чтобы запросить, чтобы определенный диапазон текста был раскрашен.

     Метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> возвращает массив значений, по одному для каждой буквы в разнохле текста. Он также определяет диапазон текста как определенный тип цветоподобного элемента, например комментарий, ключевое слово или тип данных.

3. Используйте информацию о <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> цветении, возвращенную для перекраски и отображения ее текста.

> [!NOTE]
> В дополнение к использованию colorizer языковой службы, VSPackage может выбрать для использования общего назначения Visual Studio окружающей среды SDK текстовой окраски механизма. Для получения дополнительной информации об этом механизме [см.](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)

## <a name="see-also"></a>См. также

- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Реализация цветовой маркировки синтаксиса](../extensibility/internals/implementing-syntax-coloring.md)
- [Практическое руководство. Использование встроенных цветных элементов](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Настраиваемые цветные элементы](../extensibility/internals/custom-colorable-items.md)
