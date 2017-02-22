---
title: "Пользовательские цветных элементов | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "цветные элементы"
  - "языковые службы, пользовательские цветных элементов"
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Пользовательские цветных элементов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Список типов можно переопределить для выделения цветом, например, ключевые слова и комментарии, путем реализации пользовательского цветных элементов как часть службы языка.  
  
## Параметры пользователя цветных элементов  
 Можно отобразить **шрифты и цвета** диалоговое окно, выбрав **Параметры** на **средства** меню, а затем выбрав **шрифты и цвета** под **среды**. При выборе отображения, таких как **Текстовый редактор** или **командное окно**,  **отображения элементов** список содержит все цветные элементы для отображения этого. Можно просмотреть и изменить шрифт, размер, цвет и цвет фона для каждого цветного элемента. Выбранные параметры хранятся в кэше в реестре и доступен по имени цветного элемента.  
  
## Презентация цветных элементов  
 Поскольку Интегрированной обрабатывает переопределений пользователя цветных элементов в **шрифты и цвета** диалоговом необходимо передавать только каждого пользовательского окрашиваемого элемента с именем. Это имя является то, что будет отображаться в **отображения элементов** списка. Цветные элементы отображаются в алфавитном порядке. Чтобы сгруппировать служба языка пользовательского цветных элементов, можно начать каждого имени с названием языка, например **NewLanguage \- комментарий** и **NewLanguage \- ключевое слово**.  
  
> [!CAUTION]
>  В имени цветного элемента, чтобы избежать конфликтов с существующими именами цветного элемента должно включать имя языка. Если изменить имя одного из цветных элементов во время разработки, необходимо сбросить кэш, который был создан при первом запуске невозможен, цветных элементов. Вы можете Сбросить экспериментальный кэша с помощью средства CreateExpInstance, которая устанавливается вместе с Visual Studio SDK, обычно в каталоге  
>   
>  **\\Microsoft Visual Studio C:\\Program файлы \(x86\) 14.0\\VSSDK\\VisualStudioIntegration\\Tools\\Bin**  
>   
>  Сброс параметров кэша, вызовите `CreateExpInstance /Reset`. Дополнительные сведения о CreateExpInstance см. в разделе [Служебная программа CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).  
  
 Первый элемент в списке цветных элементов никогда не указывается. Первый элемент соответствует индексу цветного элемента 0, и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] всегда предоставляет цвета текста по умолчанию и атрибуты этого элемента. Самым простым способом работы с этим элементом без ссылки является предоставить заполнитель цветного элемента в списке первым.  
  
## Реализация пользовательских цветных элементов  
  
1.  Определите, что необходимо выделение цветом на вашем языке, например ключевое слово, оператор и идентификатора.  
  
2.  Создайте эти цветных элементов перечисления.  
  
3.  Свяжите типы маркеров, возвращенный средство синтаксического анализа или сканер с перечисляемые значения.  
  
     Например значения, представляющие типы маркеров может быть одинаковые значения в перечислении пользовательских цветных элементов.  
  
4.  В своей реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод в своей <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> объекта, заполнить список атрибутов со значениями из пользовательских цветных элементов перечисления соответствующие типы маркеров, возвращенный средство синтаксического анализа или сканера.  
  
5.  В том же классе, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейса, реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> интерфейса и его два метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6.  Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
7.  Если требуется поддерживать 24\-разрядный или высоким цветовых значений, необходимо также реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейса.  
  
8.  В объект языковой службы, создайте список, содержащий ваш <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> по одному для каждого цветного элемента, можно определить средство синтаксического анализа или сканера.  
  
     Каждый элемент в списке доступны с помощью соответствующее значение из перечисления пользовательских цветных элементов. Используйте значения перечисления в качестве индекса в списке. Никогда не подключались к первый элемент в списке, так как он соответствует текст по умолчанию стиля, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] всегда обрабатывает сам. Вы можете компенсировать это, вставив цветного элемента заполнителя в начале списка.  
  
9. В своей реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> метод возвращает количество элементов в список пользовательских цветных элементов.  
  
10. В своей реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> метода возвращают запрошенный цветного элемента из списка.  
  
 Пример реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейсов, в разделе <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## См. также  
 [Модель службы языка прежних версий](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [В редакторах синтаксиса](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Синтаксиса в языковую службу для прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Реализация Цветовая подсветка синтаксиса](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Практическое руководство: использование встроенных цветных элементов](../../extensibility/internals/how-to-use-built-in-colorable-items.md)