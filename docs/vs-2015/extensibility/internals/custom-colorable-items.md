---
title: Настраиваемые цветные элементы | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fffb77788a4ac88f2ee607dd989de8c7aab8aebf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821933"
---
# <a name="custom-colorable-items"></a>Настраиваемые цветные элементы
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Список типов можно переопределить для выделения цветом, такие как ключевые слова и комментарии, путем реализации пользовательских цветных элементов как часть службы вашего языка.  
  
## <a name="user-settings-of-colorable-items"></a>Параметры пользователя цветных элементов  
 Можно отобразить **шрифты и цвета** диалоговое окно, выбрав **параметры** на **средства** меню, а затем выбрав **шрифты и цвета** в разделе **среды**. При выборе отображения, такие как **текстовый редактор** или **командное окно**, **отображаемые элементы** отображается цветных элементов для этой отображения. Можно просмотреть и изменить шрифт, размер, цвет и цвет фона для каждого цветного элемента. Выбранные параметры хранятся в кэше в реестре и доступен по имени цветного элемента.  
  
## <a name="presentation-of-colorable-items"></a>Презентации цветных элементов  
 Так как среда IDE обрабатывает переопределений пользователя цветных элементов в **шрифты и цвета** диалоговое окно, необходимо только указать каждого настраиваемого цветного элемента с именем. Это имя отображается в **отображаемые элементы** списка. Цветные элементы отображаются в алфавитном порядке. Чтобы сгруппировать службы вашего языка пользовательских цветных элементов, можно начать каждое имя именем своего языка, например **NewLanguage - комментарий** и **NewLanguage - ключевое слово**.  
  
> [!CAUTION]
>  Имя языка следует включить в имя цветного элемента, чтобы избежать конфликтов с существующими именами цветного элемента. Если изменить имя одного из цветных элементов во время разработки, необходимо сбросить кэш, который был создан в первый раз обращается к вашей цветных элементов. Вы можете Сбросить экспериментальный кэша с помощью средства CreateExpInstance, который устанавливается вместе с Visual Studio SDK, обычно в каталоге  
>   
>  **C:\Program файлы (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
>  Чтобы сбросить кэш, вызовите `CreateExpInstance /Reset`. Дополнительные сведения о CreateExpInstance, см. в разделе [CreateExpInstance Utility](../../extensibility/internals/createexpinstance-utility.md).  
  
 Первый элемент в список цветных элементов никогда не указывается. Первый элемент соответствует индекс цветного элемента, равный 0, и [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] всегда предоставляет цвета текста по умолчанию и атрибуты этого элемента. Для предоставления заполнитель цветного элемента в списке как первый элемент является самый простой способ работы с этим элементом, на которые нет ссылок.  
  
## <a name="implementing-custom-colorable-items"></a>Реализация пользовательских цветных элементов  
  
1. Определите, что необходимо цветом на вашем языке, например ключевое слово, оператор и идентификатор.  
  
2. Создайте перечисление эти цветных элементов.  
  
3. Свяжите типы маркеров, возвращен из синтаксического анализатора или сканера с помощью перечисляемые значения.  
  
    Например значения, представляющие типы маркеров может быть те же значения в перечислении пользовательских цветных элементов.  
  
4. В реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод в вашей <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> объекта, заполнить список атрибутов со значениями из соответствующих типов маркеров, возвращен из синтаксического анализатора или сканера пользовательских цветных элементов перечисления.  
  
5. В том же классе, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейса, реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> интерфейс и его два метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6. Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
7. Если вы хотите поддерживать значения цвета 24-разрядный или высокого уровня, также реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейс.  
  
8. В объект службы языка, создайте список, содержащий ваш <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> , по одному для каждого цветного элемента, можно определить синтаксического анализатора или сканера.  
  
    Каждый элемент в списке доступны посредством соответствующее значение из перечисления пользовательских цветных элементов. Используйте значения перечисления в качестве индекса в списке. Первый элемент в списке никогда не осуществляется, так как он соответствует текст по умолчанию стиль [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] всегда обрабатывает сам. Вы можете компенсировать это, вставив цветного элемента заполнителя в начале списка.  
  
9. В реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> метода, возвращает количество элементов в список пользовательских цветных элементов.  
  
10. В реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> метода возврата запрошенного цветного элемента из списка.  
  
    Пример реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейсов, см. в разделе <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## <a name="see-also"></a>См. также  
 [Модель языковой службы прежних версий](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Цветовая маркировка синтаксиса в специализированных редакторах](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Реализация цветовой маркировки синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Практическое руководство. Использование встроенных цветных элементов](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

