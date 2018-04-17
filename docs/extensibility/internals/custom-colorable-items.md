---
title: Элементы пользовательского Окрашиваемого | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b23ff39abcb9a1354ea28becab3b7df867378ddf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="custom-colorable-items"></a>Цветные настраиваемые элементы
Список типов можно переопределить для выделения цветом, такие как ключевые слова и комментарии, путем реализации пользовательского цветные элементы как часть службы языка.  
  
## <a name="user-settings-of-colorable-items"></a>Параметры пользователя цветных элементов  
 Можно отобразить **шрифты и цвета** диалоговое окно, выбрав **параметры** на **средства** меню, а затем выбрав **шрифты и цвета** в разделе **среды**. При выборе отображения, такие как **текстовый редактор** или **командное окно**, **отображения элементов** отображается цветных элементов для этого отображения. Можно просмотреть и изменить шрифт, размер, цвет и цвет фона для каждого цветного элемента. Выбранные параметры хранятся в кэше в реестре и доступен по имени цветного элемента.  
  
## <a name="presentation-of-colorable-items"></a>Презентация цветных элементов  
 Поскольку IDE обрабатывает переопределения пользователем цветных элементов в **шрифты и цвета** диалоговое окно, необходимо только указать каждого пользовательского окрашиваемого элемента с именем. Это имя является то, что будет отображаться в **отображения элементов** списка. Цветные элементы отображаются в алфавитном порядке. Для группирования пользовательских цветные элементы языковой службы, можно начать каждого имени название языка, например **NewLanguage - комментарий** и **NewLanguage - ключевое слово**.  
  
> [!CAUTION]
>  Имя языка следует включать в имя цветного элемента, чтобы избежать конфликтов с существующими именами цветного элемента. Если изменить имя одного из вашего цветных элементов во время разработки, необходимо сбросить кэш, который был создан при первом запуске невозможен, цветные элементы. Можно сбросить в экспериментальном кэш средство CreateExpInstance, которое устанавливается вместе с Visual Studio SDK, обычно в каталоге  
>   
>  **\Microsoft Visual Studio C:\Program файлы (x86) 14.0\VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
>  Чтобы сбросить кэш, вызовите `CreateExpInstance /Reset`. Дополнительные сведения о CreateExpInstance см. в разделе [CreateExpInstance программы](../../extensibility/internals/createexpinstance-utility.md).  
  
 Первый элемент в списке цветные элементы никогда не указывается. Первый элемент соответствует индексу цветного элемента 0, и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] всегда предоставляет цвета текста по умолчанию и атрибуты этого элемента. Самый простой способ работы с данного элемента без ссылок — предоставить заполнитель цветного элемента в списке первым.  
  
## <a name="implementing-custom-colorable-items"></a>Реализация пользовательских цветных элементов  
  
1.  Определите, что необходимо цветом на языке, например ключевое слово, оператор и идентификатор.  
  
2.  Создайте эти цветных элементов перечисления.  
  
3.  Свяжите типы маркеров, возвращенные синтаксического анализа или сканер с перечисляемые значения.  
  
     Например значения, представляющие типы маркера может быть одинаковые значения в перечислении цветные пользовательские элементы.  
  
4.  В реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод в вашей <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> объекта, заполнить список атрибутов из значений перечисления вашего пользовательского цветные элементы, соответствующие типам маркеров, возвращаемые из средства синтаксического анализа или сканера.  
  
5.  В том же классе, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейса, реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> интерфейса и его два метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6.  Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
7.  Если вы хотите поддерживать 24-разрядный или высокий цветовых значений, также реализуют <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейса.  
  
8.  В объект языковой службы, создайте список, содержащий ваш <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> объектов, по одному для каждого цветного элемента, можно определить средство синтаксического анализа или сканера.  
  
     Каждый элемент в списке доступны с помощью соответствующее значение из перечисления цветные пользовательские элементы. Используйте значения перечисления в качестве индекса в списке. Никогда не подключались к первый элемент в списке, так как он соответствует текст по умолчанию стиль [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] всегда обрабатывает сам. Вы можете компенсировать это, вставив цветного элемента заполнитель в начале списка.  
  
9. В реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> метод, Возврат числа элементов в список пользовательских цветных элементов.  
  
10. В реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> метод, возвращать запрошенный цветного элемента из списка.  
  
 Пример реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейсов, в разделе <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## <a name="see-also"></a>См. также  
 [Модель службы языка для прежних версий](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Синтаксис, выделение цветом в редакторах](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Синтаксиса в языковую службу прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Реализация Цветовая подсветка синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Практическое руководство. Использование встроенных цветных элементов](../../extensibility/internals/how-to-use-built-in-colorable-items.md)