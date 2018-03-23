---
title: В прежних версий языковую службу раскраску синтаксических | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2ae4ee117e43b1a3293aab932a559b3d1c822c9d
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Синтаксиса в языковую службу прежних версий

Visual Studio использует службу выделения цветом элементов языка определения и отобразить их с указанным цветов в редакторе.

## <a name="colorizer-model"></a>Модель colorizer
 Служба реализует языка <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс, который затем используется редакторами. Эта реализация представляет собой отдельный объект в службе языка, как показано на следующем рисунке:

 ![График SVC Colorizer](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
>  Служба цветовой подсветки синтаксиса отдельно от основной механизм Visual Studio для выделения цветом текста. Дополнительные сведения об общей [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] механизм поддержки выделения цветом, в разделе [использование шрифтов и цветов](../../extensibility/using-fonts-and-colors.md).

 Помимо colorizer языковой службы можно указать пользовательский цветные элементы, используемые редактором, рекламы, то он передает пользовательские цветных элементов. Это можно сделать путем реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> тот же объект, реализующий интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейс. Возвращает число пользовательских цветные элементы, когда вызывает редактор <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> метод, который возвращает отдельных пользовательского окрашиваемого объекта, когда вызывает редактор <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> метод.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Метод возвращает объект, реализующий интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> интерфейс. Если языковая служба поддерживает 24-разрядный или высокий цветовых значений, он должен реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейса на один и тот же объект как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> интерфейса.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Использование службы языка Colorizer VSPackage

1.  Пакет VSPackage должен получить в соответствующую языковую службу, которая требует языковой службы VSPackage для выполнения следующих:

    1.  Используйте объект, реализующий интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> интерфейс для получения текста, чтобы быть цветом.

         Обычно текст отображается с использованием объекта, реализующего <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейса.

    2.  Получите языковой службы с помощью запроса к поставщику службы VSPackage для GUID языковой службы. Языковые службы определяются в реестре по расширению файла.

    3.  Связать с языковой службы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> путем вызова его <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> метод.

2.  Пакет VSPackage можно получить и использовать объект colorizer следующим образом:

    > [!NOTE]
    > Пакеты VSPackage, использующих базового редактора не следует явным образом получить объекты colorizer службы языка. Как только экземпляр базового редактора получает соответствующую языковую службу, он выполняет все задачи выделение цветом, показано ниже.

    1.  Получить объект colorizer языковой службы, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>, и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> интерфейсов путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> метод службы языка <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> объекта.

    2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод, чтобы получить сведения о colorizer для определенного диапазона текста.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Возвращает массив значений, один для каждого символа в текстовом диапазоне выделение цветом. Значения являются индексы в список цветного элемента обслуживается базового редактора списка цветного элемента по умолчанию или пользовательского окрашиваемого элемента списка, поддерживаемого языка самой службы.

    3.  Выделение цветом сведения, возвращенные <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод для отображения выбранного текста.

> [!NOTE]
>  Помимо использования colorizer языковой службы, пакет VSPackage также можно использовать универсальный механизм цветовой подсветки текста Visual Studio. Дополнительные сведения о механизме см. в разделе [использование шрифтов и цветов](../../extensibility/using-fonts-and-colors.md).

## <a name="in-this-section"></a>В этом разделе
 [Реализация Цветовая подсветка синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md) описание, как редактор получает доступ к языковую службу Цветовая подсветка синтаксиса и языковой службы необходимо реализовать для поддержки Цветовая подсветка синтаксиса.

 [Как: Используйте встроенные цветные элементы](../../extensibility/internals/how-to-use-built-in-colorable-items.md) показано, как использовать встроенные цветные элементы из языковой службы.

 [Пользовательские цветные элементы](../../extensibility/internals/custom-colorable-items.md) описывает, как реализовать пользовательский цветных элементов.

## <a name="see-also"></a>См. также

- [Шрифты и цвета](../../extensibility/using-fonts-and-colors.md)