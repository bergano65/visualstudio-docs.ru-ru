---
title: Выделение синтаксиса в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59d25c338cb0c7406c533afeceaf3675fbd16e96
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842937"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Цветовая маркировка синтаксиса в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] использует службу цветов для распознавания элементов языка и отображения их с указанными цветами в редакторе.  
  
## <a name="colorizer-model"></a>Модель тонирования  
 Языковая служба реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс, который затем используется редакторами. Эта реализация является отдельным объектом из языковой службы, как показано на следующем рисунке.  
  
 ![График SVC Colorizer](../../extensibility/internals/media/figlgsvccolorizer.gif "фиглгсвкколоризер")  
Простая модель тонирования  
  
> [!NOTE]
> Служба цветового выделения синтаксиса отличается от общего [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] механизма выделения цветом текста. Дополнительные сведения об общем [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] механизме, поддерживающем окраска, см. в разделе [Использование шрифтов и цветов](../../extensibility/using-fonts-and-colors.md).  
  
 Помимо тонирования, языковая служба может предоставлять настраиваемые цветовые элементы, используемые редактором, составлять объявления о том, что он предоставляет настраиваемые цветные элементы. Это можно сделать, реализовав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> интерфейс для того же объекта, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейс. Он возвращает число настраиваемых цветовых элементов, когда редактор вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> метод, и возвращает отдельный настраиваемый цветовой элемент, когда редактор вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> метод.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>Метод возвращает объект, реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> интерфейс. Если языковая служба поддерживает 24-разрядные или высокие значения цвета, она должна реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейс для того же объекта, что и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> интерфейс.  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Как VSPackage использует цветовой цвет языковой службы  
  
1. Пакет VSPackage должен получить соответствующую языковую службу, которая требует пакета VSPackage языковой службы, чтобы выполнить следующие действия:  
  
    1. Используйте объект, реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> интерфейс, чтобы получить текст для выделения цветом.  
  
         Текст обычно отображается с помощью объекта, реализующего <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейс.  
  
    2. Получите языковую службу, запросив поставщика служб VSPackage для идентификатора GUID языковой службы. Языковые службы определяются в реестре по расширению файла.  
  
    3. Свяжите языковую службу с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> , вызвав ее <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> метод.  
  
2. Пакет VSPackage теперь может получить и использовать объект «окраска» следующим образом:  
  
    > [!NOTE]
    > Пакеты VSPackage, использующие основной редактор, не должны явным образом получать объекты цветовой службы языка. Как только экземпляр базового редактора получает соответствующую языковую службу, он выполняет все задачи выделения цветом, показанные здесь.  
  
    1. Получите объект языковой поддержки, который реализует `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` интерфейсы, и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> , вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> метод в объекте языковой службы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .  
  
    2. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод, чтобы получить сведения о параметрах выделения цветом для определенного фрагмента текста.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Возвращает массив значений, по одному для каждого символа в цветовом диапазоне текста. Значения — это индексы в списке элементов с цветовым списком, который является либо списком элементов по умолчанию, поддерживаемым основным редактором, либо настраиваемым списком элементов, поддерживаемым самой языковой службой.  
  
    3. Используйте сведения о цветовой отсчете, возвращаемые <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> методом для вывода выбранного текста.  
  
> [!NOTE]
> Помимо использования цветового интерфейса языковой службы, VSPackage также может использовать механизм выделения текста общего назначения [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Дополнительные сведения об этом механизме см. [в разделе Использование шрифтов и цветов](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Реализация цветовой маркировки синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)  
 Описывает, как редактор обращается к цветовой маркировке синтаксиса языковой службы и какую языковую службу необходимо реализовать для поддержки цветового выделения синтаксиса.  
  
 [Практическое руководство. Использование встроенных цветных элементов](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Демонстрирует использование встроенных цветовых элементов из языковой службы.  
  
 [Настраиваемые цветные элементы](../../extensibility/internals/custom-colorable-items.md)  
 Обсуждается реализация пользовательских цветовых элементов.  
  
## <a name="see-also"></a>См. также:  
 [Использование шрифтов и цветов](../../extensibility/using-fonts-and-colors.md)
