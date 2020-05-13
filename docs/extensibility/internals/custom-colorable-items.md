---
title: Пользовательские цветные предметы Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: feecd9e8f8178045f66999b775e2d0792f50b288
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708998"
---
# <a name="custom-colorable-items"></a>Пользовательские цветные элементы
Список типов для раскраскивания можно переопределить, например ключевые слова и комментарии, реализовав пользовательские цветные элементы как часть языковой службы.

## <a name="user-settings-of-colorable-items"></a>Пользовательские настройки цветных элементов
 Вы можете отобразить диалоговую коробку **шрифтов и цветов,** выбрав **параметры** в меню **«Инструменты»,** а затем выбрав **шрифты и цвета** в **среде.** При выборе дисплея, **например, text Editor** или **Командное окно,** в поле списка **элементов дисплея** отображаются все цветные элементы для этого дисплея. Вы можете просматривать и изменять шрифт, размер, цвет переднего плана и цвет фона для каждого цветного элемента. Ваш выбор хранится в кэше в реестре и доступен под именем товара.

## <a name="presentation-of-colorable-items"></a>Презентация цветных элементов
 Поскольку IDE обрабатывает пользователем переопределения цветных элементов в диалоговом поле **шрифтов и цветов,** вам нужно только предоставить каждый пользовательский цветной элемент с именем. Это имя — это то, что отображается в списке **элементов Display.** Цветные элементы отображаются в алфавитном порядке. Чтобы сгруппировать пользовательские цветные элементы вашего языкового сервиса, вы можете начать каждое имя с вашего имени языка, например **NewLanguage - Комментарий** и **NewLanguage - Ключевое слово.**

> [!CAUTION]
> Чтобы избежать столкновений с существующими цветными именами элементов, необходимо включить имя языка в имя товара, чтобы избежать столкновений с существующими цветными именами элементов. Если во время разработки вы измените имя одного из ваших colorable элементов, необходимо сбросить кэш, созданный при первом доступе к красятным элементам. Экспериментальный кэш можно сбросить с помощью инструмента **CreateExpInstance,** который устанавливается с помощью Visual Studio SDK, как правило, в каталоге:
>
> *C:-Программные файлы (x86)»Microsoft Visual Studio 14.0'VSSDK-VisualStudioIntegration*
>
> Чтобы сбросить кэш, введите **CreateExpInstance /Reset.** Для получения дополнительной информации о **CreateExpInstance**, [см.](../../extensibility/internals/createexpinstance-utility.md)

 Первый элемент в списке цветных элементов никогда не упоминается. Первый элемент соответствует цветообразу индексу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 0 и всегда поставляет цвета текста по умолчанию и атрибуты для этого элемента. Самый простой способ борьбы с этим неупомянутым пунктом является поставка заполнителя colorable пункта в вашем списке в качестве первого пункта.

## <a name="implement-custom-colorable-items"></a>Реализация пользовательских цветных элементов

1. Определите, что должно быть раскрашиваться на вашем языке, например, ключевое слово, оператор и идентификатор.

2. Создайте перечисление этих цветных элементов.

3. Ассоциированные типы токенов, возвращенные из парсера или сканера с перечисленными значениями.

    Например, значения, представляющие типы маркеров, могут быть одинаковыми значениями в пользовательских цветовых элементах, перечисленных в перечислении.

4. При реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> в объекте заполните список атрибутов значениями из пользовательских цветовых элементов, соответствующих типам токенов, возвращенным из парсера или сканера.

5. В том же классе, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> интерфейс, реализуем интерфейс и два его метода, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.

6. Реализуйте интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

7. Если вы хотите поддерживать 24-битные или высокие <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> значения цвета, также реализовать интерфейс.

8. В объекте языковой службы создайте список, содержащий объекты, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> по одному для каждого цветного элемента, который может идентифицировать ваш парорер или сканер.

    Вы можете получить доступ к каждому элементу в списке, используя соответствующее значение из пользовательских цветовых элементов перечисления. Используйте значения перечисления в качестве индекса в списке. Первый элемент в списке никогда не доступен, потому [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] что он соответствует стилю текста по умолчанию, который всегда обрабатывает себя. Вы можете компенсировать это, вставив заполнитель цветной элемент в начале списка.

9. В реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> метода верните количество элементов в списке пользовательских цветных элементов.

10. При реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> метода верните запрошенный цветной элемент из списка.

    Например, как реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> интерфейсы и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>интерфейсы, см.

## <a name="see-also"></a>См. также
- [Модель устаревшего языкового сервиса](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Синтаксис раскраски в пользовательских редакторов](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Раскраска Syntax в устаревшей языковой службе](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Реализация окраски синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)
- [Как: Использование встроенных цветных элементов](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
