---
title: Цветовая маркировка синтаксиса в специализированных редакторах | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f82902ebcb82ea311617d3a7a767c5dabaedd311
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53886654"
---
# <a name="syntax-coloring-in-custom-editors"></a>Цветовая маркировка синтаксиса в специализированных редакторах
Редакторы Visual Studio пакет SDK для среды, включая базовый редактор, использование служб языка, для идентификации определенных синтаксических элементов и их отображения с указанными цветами для представления данного документа.

## <a name="colorization-requirements"></a>Требования к цветовое выделение
 Все редакторы, реализация палитру языковой службы необходимо:

1.  Использовать объект, реализующий интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> для управления текст, который необходимо выделить цветом и объект, реализующий интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для предоставления документа представления текста.

2.  Получите интерфейс для определенной службы языка через запрос к поставщику службы в пакете VSPackage, с помощью службы языков идентификатору GUID.

3.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> метод объекта, реализующего <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Этот метод связывает службы языка с <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> реализацию VSPackage, используется для управления текст, который необходимо выделить цветом.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Использование палитру языковой службы базовым редактором
 Когда службы языка с палитры получается путем экземпляр базового редактора, синтаксического анализа и визуализации текста с помощью палитры языковой службы происходит автоматически, не требуя какого-либо дальнейшего вмешательства со стороны пользователя.

 Интегрированная среда разработки прозрачно:

-   Вызывает палитры при необходимости для анализа и анализа текста, так как он добавляется или изменяется в реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.

-   Гарантирует, что отображение, предоставляемые представления документов, предоставляемых <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> реализации обновляются и перерисована, используя сведения, возвращаемые функцией палитры.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Использование редактора неосновных палитру языковой службы
 Экземпляры не базовый редактор можно также использовать службы цветовое выделение синтаксиса языковой службы, но их необходимо явным образом получить и применить палитры службы и перерисовать свои представления документа, сами.

 Чтобы сделать это, редактор неосновных необходимо:

1.  Получить объект палитру языковой службы (который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). VSPackage делает это путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> метод в интерфейсе языковой службы.

2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод для запроса, что определенный диапазон текста, необходимо выделить цветом.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Метод возвращает массив значений, одной для каждой буквы в тексте span выделение цветом. Она также определяет диапазон текста, как определенный тип цветного элемента, например комментарий, ключевое слово или тип данных.

3.  Использовать цветовое выделение сведения, возвращаемые функцией <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> для перерисовки и отображения текста.

> [!NOTE]
> Помимо использования палитры языковой службы, пакет VSPackage можно с использованием механизма общего назначения выделение цветом текста пакета SDK для среды Visual Studio. Дополнительные сведения о механизме, см. в разделе [использование шрифтов и цветов](../extensibility/using-fonts-and-colors.md).

## <a name="see-also"></a>См. также

- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Реализация цветовой маркировки синтаксиса](../extensibility/internals/implementing-syntax-coloring.md)
- [Практическое руководство. Использование встроенных цветных элементов](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Настраиваемые цветные элементы](../extensibility/internals/custom-colorable-items.md)