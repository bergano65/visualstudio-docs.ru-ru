---
title: Общие цвета Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 9d3186f3-07d2-441f-b33e-435e95d8a0b8
caps.latest.revision: 11
ms.author: brgeorge
ms.openlocfilehash: 421ff85831bb611b655de2bc35f01423b61921a2
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301317"
---
# <a name="shared-colors"></a>Общие цвета
Вставьте сюда введение.  
  
## <a name="shared-colors"></a>Общие цвета  
 Если вы разрабатываете пользовательский интерфейс, в котором используются стандартные элементы оболочки Visual Studio, или вам нужно обеспечить согласованность элемента интерфейса с аналогичными функциями, используйте существующие имена токенов в файлах определения пакетов для выбора и назначения цветов. Таким образом можно обеспечить согласованность пользовательского интерфейса со всей средой Visual Studio и его автоматическое обновление при добавлении или обновлении тем.  
  
 В этом разделе описываются стандартные элементы пользовательского интерфейса и используемые ими имена токенов, на которые можно ссылаться при разработке похожего пользовательского интерфейса. Более подробные сведения о доступе к этим токенам цветов см. в разделе [The VSColor Service](../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Используйте имена токенов правильно.  
  
- **Используйте имена токенов в соответствии с функцией, а не самим цветом.** Стандартные общие цвета связаны с определенными элементами интерфейса и предназначены для использования только для аналогичных или похожих функций. Например, не используйте цвет выбранного поля со списком для анимированного индикатора хода выполнения только потому, что вам понравился цвет. Функции поля со списком и анимированного индикатора различны, и если цвет, связанный с полем со списком, изменится, он может оказаться неподходящим для анимированного элемента. Согласованное использование цветов помогает пользователям ориентироваться в интерфейсе и предотвращает путаницу.  
  
- **Используйте цвета фона и текста в правильном сочетании.** Цвет фона, предназначенный для текста, имеет соответствующий цвет текста. Не используйте цвета текста, отличные от тех, которые определены для данного цвета фона. Если с цветом фона не связан цвет текста, не используйте его для поверхности, на которой будет выводиться текст. Другие сочетания цветов текста и фона могут сделать интерфейс неудобным для восприятия.  
  
- **Используйте цвета элементов управления, соответствующие их расположению.** В определенных состояниях некоторые элементы управления Visual Studio не имеют отдельных цветов границ и фона. Эти цвета наследуются от областей, в которых они расположены. Всегда используйте имена токенов, которые подходят для того места, в котором вы размещаете элементы управления.  
  
> [!IMPORTANT]
> Не используйте токены из категорий "Начальная страница" и "Cider"!  
  
### <a name="command-structures"></a>Структура команд  
  
#### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Меню  
 Меню встречаются в Visual Studio 2013 в нескольких местах. Они могут находиться в главной строке меню, внедряться в окна документов или инструментов или вызываться при щелчке правой кнопкой мыши различным элементам интегрированной среды разработки. Реализация меню, связанных с другими элементами пользовательского интерфейса, рассматривается в разделах, посвященных соответствующим элементам. Всегда используйте стандартную реализацию меню, предоставляемую средой Visual Studio. Однако в некоторых редких случаях доступ к стандартным меню Visual Studio может отсутствовать. В таких ситуациях используйте указанные ниже имена токенов для обеспечения согласованности пользовательского интерфейса с другими меню в Visual Studio.  
  
 ![Красная линия меню](../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303-000_MenuRedline")  
  
Используйте:  
- если нужно создать пользовательское меню;  
  
- если есть новый компонент пользовательского интерфейса, который должен соответствовать меню Visual Studio.  
  
Не используйте:  
цвет фона сам по себе. Всегда используйте определенное сочетание цвета фона и цвета переднего плана.  
  
##### <a name="menu-title"></a>Заголовок меню  
 Заголовок меню состоит из фона, границы и текста заголовка, а также необязательного глифа (обычно если меню находится на панели команд).  
  
 ![Красная линия заголовка меню](../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303-001_MenuTitleRedline")  
  
Используйте:  
при создании пользовательского заголовка меню.  
  
Не используйте:  
- для каких-либо элементов, которые не должны всегда соответствовать заголовку меню;  
  
- в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.  
  
  **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Заголовок меню по умолчанию](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Заголовок меню**|Историческая справка|None|  
|![Заголовок меню по умолчанию](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Заголовок меню**|Передний план (текст)|`Environment.CommandBarTextActive`|  
|![Заголовок меню с глифом по умолчанию](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Заголовок меню с глифом**|Передний план (глиф)|`Environment.CommandBarMenuGlyph`|  
|![Заголовок меню с глифом по умолчанию](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Заголовок меню с глифом**|Граница|None|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Заголовок меню при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Заголовок меню**|Историческая справка|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Заголовок меню при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Заголовок меню**|Передний план (текст)|`Environment.CommandBarTextHover`|  
|![Заголовок меню с глифом при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Заголовок меню с глифом**|Передний план (глиф)|`Environment.CommandBarMenuMouseOverGlyph`|  
|![Заголовок меню с глифом при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Заголовок меню с глифом**|Граница|`Environment.CommandBarBorder`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Активная кнопка заголовка меню](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Заголовок меню**|Историческая справка|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Активная кнопка заголовка меню](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Заголовок меню**|Передний план (текст)|`Environment.CommandBarTextActive`|  
|![Активная кнопка заголовка меню с глифом](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Заголовок меню с глифом**|Передний план (глиф)|`Environment.CommandBarMenuMouseDownGlyph`|  
|![Активная кнопка заголовка меню с глифом](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Заголовок меню с глифом**|Граница|`Environment.CommandBarMenuBorder`<br /><br /> Только с левой, верхней и правой сторон.|  
  
 **Отключен**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Неактивная кнопка заголовка меню с глифом](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Заголовок меню с глифом**|Историческая справка|None|  
|![Неактивная кнопка заголовка меню с глифом](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Заголовок меню с глифом**|Передний план (текст)|`Environment.CommandBarTextInactive`|  
|![Неактивная кнопка заголовка меню с глифом](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Заголовок меню с глифом**|Передний план (глиф)|`Environment.CommandBarTextInactive`|  
|![Неактивная кнопка заголовка меню с глифом](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Заголовок меню с глифом**|Граница|None|  
  
##### <a name="menu"></a>Меню  
 Отдельный пункт меню состоит из текста и необязательных значка, флажка или глифа подменю. Его цвета фона и текста меняются при наведении указателя. Этот токен цвета представляет собой пару, состоящую из цвета фона и цвета переднего плана.  
  
 ![Красная линия пунктов меню](../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303-009_MenuItemRedline")  
  
 Используйте:  
 для любого раскрывающегося списка, открывающегося из строки меню или панели команд.  
  
Не используйте:  
- для любого раскрывающегося списка, открывающегося в другом контексте;  

- в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.  
  
  **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Меню по умолчанию](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Меню**|Историческая справка|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Меню по умолчанию](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Меню**|Передний план (текст)|`Environment.CommandBarTextActive`|  
|![Меню по умолчанию](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Меню**|Передний план (глиф подменю)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Меню по умолчанию](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Меню**|Граница|`Environment.CommandBarMenuBorder`|  
|![Меню по умолчанию](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Меню**|Фон канала значка|`Environment.CommandBarMenuIconBackground`|  
|![Меню по умолчанию](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Меню**|Разделитель|`Environment.CommandBarMenuSeparator`|  
|![Меню по умолчанию](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Меню**|Shadow|`Environment.DropShadowBackground`|  
|![Меню с установленным флажком](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Проверил**|Флажок|`Environment.CommandBarCheckBox`|  
|![Меню с установленным флажком](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Проверил**|Фон флажка|`Environment.CommandBarSelectedIcon`|  
|![Выбранное меню](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Выбрано**|Фон значка|`Environment.CommandBarSelected`|  
|![Выбранное меню](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Выбрано**|Граница значка|`Environment.CommandBarSelectedBorder`|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Меню при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Элемент меню**|Историческая справка|`Environment.CommandBarMenuItemMouseOver`|  
|![Меню при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Элемент меню**|Передний план (текст)|`Environment.CommandBarMenuItemMouseOver`|  
|![Меню при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Элемент меню**|Передний план (глиф подменю)|`Environment.CommandBarMenuMouseOverSubmenuGlyph`|  
|![Меню при наведении курсора мыши с установленным флажком ](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Проверил**|Флажок|`Environment.CommandBarCheckBoxMouseOver`|  
|![Меню при наведении курсора мыши с установленным флажком ](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Проверил**|Фон флажка|`Environment.CommandBarHoverOverSelectedIcon`|  
|![Выбранное меню при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Выбрано**|Фон значка|`Environment.CommandBarHoverOverSelected`|  
|![Выбранное меню при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Выбрано**|Граница значка|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Отключен**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Неактивное меню](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Элемент меню|Передний план (текст)|`Environment.CommandBarTextInactive`|  
|![Неактивное меню](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Элемент меню|Передний план (глиф подменю)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Неактивное меню с установленным флажком](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Флажок установлен|Флажок|`Environment.CommandBarCheckBoxDisabled`|  
|![Неактивное меню с установленным флажком](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Флажок установлен|Фон флажка|`Environment.CommandBarSelectedIconDisabled`|  
  
#### <a name="command-bar"></a>Панель команд  
 Панель команд может встречаться в интегрированной среде разработки Visual Studio в нескольких местах. В первую очередь это командная полка и окна инструментов и документов.  
  
 Как правило, следует всегда использовать стандартную реализацию панели команд, предоставляемую средой Visual Studio. Использование стандартного механизма обеспечивает правильное отображение визуальных элементов и согласованное поведение интерактивных элементов и других элементов управления панели команд Visual Studio. Однако если вам необходимо создать собственную панель команд, следует правильно оформить ее с помощью указанных ниже имен токенов.  
  
 ![Красная линия командной строки](../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303-018_CommandBarRedline")  
  
 ![Красная линия кнопки переполнения](../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303-019_OverflowButtonRedline")  
  
 Используйте:  
 в местах, где требуется внедренная панель команд, но нельзя использовать стандартную реализацию панели команд Visual Studio.  
  
Не используйте:  
- для элементов пользовательского интерфейса, которые не похожи на панель команд;  

- для компонентов панели команд, отличных от тех, для которых определены имена токенов.  
  
##### <a name="command-bar-group"></a>Группа панели команд  
 Группа панели команд состоит из связанного набора элементов управления панели команд и может содержать любое количество кнопок, разворачивающихся кнопок, раскрывающихся меню, полей со списками или меню. Цвета этих элементов управления определяются отдельными именами токенов, которые рассматриваются в других частях этого руководства. Разделительная линия служит для разделения группы на панели команд в связанные подгруппы.  
  
 ![Групповая красная линия командной строки](../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303-020_CommandBarGroupRedline")  
  
 Используйте:  
 в местах, где требуется внедренная панель команд, но нельзя использовать стандартную реализацию панели команд Visual Studio.  
  
Не используйте:  
- для элементов пользовательского интерфейса, которые не похожи на панель команд;  

- для компонентов панели команд, отличных от тех, для которых определены имена токенов.  
  
  **По умолчанию** (нет других состояний)  
  
|Элемент|Имя токена: Category.color|  
|-------------|--------------------------------|  
|Историческая справка|`Environment.CommandBarGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|Граница|`Environment.CommandBarToolBarBorder`|  
|Маркер перетаскивания|`Environment.CommandBarDragHandle`|  
|Разделитель|`Environment.CommandBarToolBarSeparator`<br /><br /> `Environment.CommandBarToolBarSeparatorHighlight`|  
  
##### <a name="command-icons"></a>Значки команд  
 ![Красная линия значка команды](../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303-021_CommandIconRedline1")  
  
 ![Красная линия значка команды](../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303-022_CommandIconRedline2")  
  
 Используйте:  
 для кнопок, которые будут размещаться на панели команд.  
  
Не используйте:  
- для элементов управления, которые имеют собственные имена токенов;  

- в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.  
  
  **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Значок команды по умолчанию](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **По умолчанию**|Историческая справка|Н/Д (наследуется от фона панели команд)|  
|![Значок команды по умолчанию](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **По умолчанию**|Передний план (текст)|`Environment.CommandBarTextActive`|  
|![Значок команды по умолчанию](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **По умолчанию**|Граница|Недоступно|  
|![Выбранный значок команды по умолчанию](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Выбрано**|Историческая справка|`Environment.CommandBarSelected`|  
|![Выбранный значок команды по умолчанию](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Выбрано**|Передний план (текст)|`Environment.CommandBarTextSelected`|  
|![Выбранный значок команды по умолчанию](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Выбрано**|Граница|`Environment.CommandBarSelectedBorder`|  
  
 **Наведение указателя мыши и получение фокуса с клавиатуры**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Значок команды при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Стандартный при наведении указателя мыши**|Историческая справка|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Значок команды при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Стандартный при наведении указателя мыши**|Передний план (текст)|`Environment.CommandBarTextHover`|  
|![Значок команды при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Стандартный при наведении указателя мыши**|Граница|`Environment.CommandBarBorder`|  
|![Выбранный значок команды при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Выбор при наведении указателя мыши**|Историческая справка|`Environment.CommandBarHoverOverSelected`|  
|![Выбранный значок команды при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Выбор при наведении указателя мыши**|Передний план (текст)|`Environment.CommandBarTextHoverOverSelected`|  
|![Выбранный значок команды при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Выбор при наведении указателя мыши**|Граница|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Активный значок команды](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Активный значок команды**|Историческая справка|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Активный значок команды](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Активный значок команды**|Передний план (текст)|`Environment.CommandBarTextMouseDown`|  
|![Активный значок команды](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Активный значок команды**|Граница|`Environment.CommandBarBorder`|  
  
 **Отключен**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Неактивный значок команды](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Неактивный значок команды**|Историческая справка|Н/Д (наследуется от фона панели команд)|  
|![Неактивный значок команды](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Неактивный значок команды**|Передний план (текст)|`Environment.CommandBarTextInactive`|  
|![Неактивный значок команды](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Неактивный значок команды**|Граница|Недоступно|  
  
##### <a name="combo-box"></a><a name="BKMK_CommandComboBox"></a>Комбо-коробка  
  
> [!IMPORTANT]
> Поле со списком похоже на раскрывающийся список, но включает область для ввода и редактирования текста. Если раскрывающийся список не включает область для ввода и редактирования текста, используйте токены цветов, указанные в разделе [Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown).  
  
 ![Красная линия поля со списком](../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303-029_ComboBoxRedline")  
  
Используйте:  
- при создании пользовательских полей со списками;  

- при создании элемента управления панели команд, похожего на поле со списком.  

Не используйте:  
- для каких-либо элементов, которые не должны всегда соответствовать пользовательскому интерфейсу панели команд;  

- если есть доступ к оформленному полю со списком.  
  
  **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Поле ввода поля со списком](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Поле ввода**|Историческая справка|`Environment.ComboBoxBackground`|  
|![Поле ввода поля со списком](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Поле ввода**|Передний план (текст)|`Environment.ComboBoxText`|  
|![Поле ввода поля со списком](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Поле ввода**|Граница|`Environment.ComboBoxBorder`|  
|![Поле ввода поля со списком](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Поле ввода**|Разделитель|Без разделителя|  
|![Комбо окно падение&#45;вниз кнопку](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Кнопка раскрывающегося списка**|Историческая справка|Н/Д (наследуется)|  
|![Комбо окно падение&#45;вниз кнопку](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Кнопка раскрывающегося списка**|Передний план (глиф)|`Environment.ComboBoxGlyph`|  
|![Комбо-коробка&#47;падение&#45;вниз список](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Выпадающий список**|Историческая справка|`Environment.ComboBoxPopupBackgroundBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Комбо-коробка&#47;падение&#45;вниз список](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Выпадающий список**|Передний план (текст)|`Environment.ComboBoxItemText`|  
|![Комбо-коробка&#47;падение&#45;вниз список](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Выпадающий список**|Граница|`Environment.ComboBoxPopupBorder`|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Поле ввода поля со списком при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Поле ввода**|Историческая справка|`Environment.ComboBoxMouseOverBackgroundBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Поле ввода поля со списком при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Поле ввода**|Передний план (текст)|`Environment.ComboBoxMouseOverText`|  
|![Поле ввода поля со списком при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Поле ввода**|Граница|`Environment.ComboBoxMouseOverBorder`|  
|![Поле ввода поля со списком при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Поле ввода**|Разделитель|`Environment.ComboBoxMouseOverSeparator`|  
|![Комбо-коробка&#47;падение&#45;кнопку вниз на нависшие](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Кнопка раскрывающегося списка**|Историческая справка|`Environment.ComboBoxButtonMouseOverBackground`|  
|![Комбо-коробка&#47;падение&#45;кнопку вниз на нависшие](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Кнопка раскрывающегося списка**|Передний план (глиф)|`Environment.ComboBoxMouseOverGlyph`|  
|![Комбо-коробка&#47;падение&#45;вниз список на нависшие](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Выпадающий список**|Фон (пункт меню)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Комбо-коробка&#47;падение&#45;вниз список на нависшие](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Выпадающий список**|Передний план (текст)|`Environment.ComboBoxItemMouseOverText`|  
|![Комбо-коробка&#47;падение&#45;вниз список на нависшие](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Выпадающий список**|Граница (пункт меню)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Focused**  
  
|Компонент|Элемент|Имя токена: Цвет.категория|  
|---------------|-------------|--------------------------------|  
|![Поле ввода поля со списком с фокусом ввода](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Поле ввода**|Историческая справка|`Environment.ComboBoxFocusedBackground`|  
|![Поле ввода поля со списком с фокусом ввода](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Поле ввода**|Передний план (текст)|`Environment.ComboBoxFocusedText`|  
|![Поле ввода поля со списком с фокусом ввода](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Поле ввода**|Граница|`Environment.ComboBoxFocusedBorder`|  
|![Поле ввода поля со списком с фокусом ввода](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Поле ввода**|Разделитель|`Environment.ComboBoxFocusedButtonSeparator`|  
|![Комбо-коробка&#47;падение&#45;вниз кнопку сосредоточены](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Кнопка раскрывающегося списка**|Историческая справка|`Environment.ComboBoxFocusedButtonBackground`|  
|![Комбо-коробка&#47;падение&#45;вниз кнопку сосредоточены](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Кнопка раскрывающегося списка**|Передний план (глиф)|`Environment.ComboBoxFocusedGlyph`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Цвет.категория|  
|---------------|-------------|--------------------------------|  
|![Активное поле ввода поля со списком](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Поле ввода**|Историческая справка|`Environment.ComboBoxMouseDownBackground`|  
|![Активное поле ввода поля со списком](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Поле ввода**|Передний план (текст)|`Environment.ComboBoxMouseDownText`|  
|![Активное поле ввода поля со списком](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Поле ввода**|Граница|`Environment.ComboBoxMouseDownBorder`|  
|![Активное поле ввода поля со списком](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Поле ввода**|Разделитель|`Environment.ComboBoxMouseDownSeparator`|  
|![Комбо-бокс&#47;падение&#45;кнопку вниз нажатия](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Кнопка раскрывающегося списка**|Историческая справка|`Environment.ComboBoxButtonMouseDownBackground`|  
|![Комбо-бокс&#47;падение&#45;кнопку вниз нажатия](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Кнопка раскрывающегося списка**|Передний план (глиф)|`Environment.ComboBoxMouseDownGlyph`|  
  
 **Отключен**  
  
|Компонент|Элемент|Имя токена: Цвет.категория|  
|---------------|-------------|--------------------------------|  
|![Неактивное поле ввода поля со списком](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Поле ввода**|Историческая справка|`Environment.ComboBoxDisabledBackground`|  
|![Неактивное поле ввода поля со списком](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Поле ввода**|Передний план (текст)|`Environment.ComboBoxDisabledText`|  
|![Неактивное поле ввода поля со списком](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Поле ввода**|Граница|`Environment.ComboBoxDisabledBorder`|  
|![Неактивное поле ввода поля со списком](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Поле ввода**|Разделитель|Без разделителя|  
|![Комбо-бокс&#47;падение&#45;вниз кнопку отключена](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Кнопка раскрывающегося списка**|Историческая справка|None|  
|![Комбо-бокс&#47;падение&#45;вниз кнопку отключена](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Кнопка раскрывающегося списка**|Передний план (глиф)|`Environment.ComboBoxDisabledGlyph`|  
  
##### <a name="drop-down"></a><a name="BKMK_CommandDropDown"></a>Выпадение вниз  
  
> [!IMPORTANT]
> Раскрывающийся список похож на поле со списком, но не имеет области для ввода и редактирования текста. Если раскрывающийся список включает область для ввода и редактирования текста, используйте токены цветов, указанные в разделе [Combo box](../misc/shared-colors.md#BKMK_CommandComboBox).  
  
 ![Падение&#45;вниз по красной линии](../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303-042_DropdownRedline")  
  
 Используйте:  
 при создании пользовательских элементов управления типа "раскрывающийся список".  
  
Не используйте:  
- для каких-либо элементов, отличных от раскрывающегося списка;  

- для полей со списками или разворачивающихся кнопок.  
  
  **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Падение&#45;вниз поле выбора](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Поле выбора**|Историческая справка|`Environment.DropDownBackground`|  
|![Падение&#45;вниз поле выбора](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Поле выбора**|Передний план (текст)|`DropDownText`|  
|![Падение&#45;вниз поле выбора](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Поле выбора**|Граница|`DropDownBorder`|  
|![Падение&#45;вниз поле выбора](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Поле выбора**|Разделитель|Без разделителя|  
|![Кнопка «Падение&#45;»](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Кнопка раскрывающегося списка**|Историческая справка|None|  
|![Кнопка «Падение&#45;»](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Кнопка раскрывающегося списка**|Передний план (глиф)|`Environment.DropDownGlyph`|  
|![Падение&#45;вниз список](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Выпадающий список**|Историческая справка|`Environment.DropDownPopupBackgroundBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Падение&#45;вниз список](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Выпадающий список**|Передний план (текст)|`Environment.ComboBoxItemText`|  
|![Падение&#45;вниз список](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Выпадающий список**|Граница|`Environment.DropDownPopupBorder`|  
|![Падение&#45;вниз список](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Выпадающий список**|Shadow|`Environment.DropShadowBackground`|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Падение&#45;вниз по месту отбора на нависшие](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Поле выбора**|Историческая справка|`Environment.DropDownMouseOverBackgroundBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Падение&#45;вниз по месту отбора на нависшие](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Поле выбора**|Передний план (текст)|`Environment.DropDownMouseOverText`|  
|![Падение&#45;вниз по месту отбора на нависшие](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Поле выбора**|Граница|`Environment.DropDownMouseOverBorder`|  
|![Падение&#45;вниз по месту отбора на нависшие](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Поле выбора**|Разделитель|`Environment.DropDownButtonMouseOverSeparator`|  
|![Кнопка drop&#45;вниз на нависнуть](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Кнопка раскрывающегося списка**|Историческая справка|`Environment.DropDownButtonMouseOverBackground`|  
|![Кнопка drop&#45;вниз на нависнуть](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Кнопка раскрывающегося списка**|Передний план (глиф)|`Environment.DropDownMouseOverGlyph`|  
|![Падение&#45;вниз список на нависшие](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Выпадающий список**|Фон (пункт меню)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Падение&#45;вниз список на нависшие](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Выпадающий список**|Передний план (текст)|`Environment.ComboBoxItemMouseOverText`|  
|![Падение&#45;вниз список на нависшие](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Выпадающий список**|Граница (пункт меню)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Падение&#45;вниз по месту выбора нажата](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Поле выбора**|Историческая справка|`Environment.DropDownMouseDownBackground`|  
|![Падение&#45;вниз по месту выбора нажата](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Поле выбора**|Передний план (текст)|`Environment.DropDownMouseDownText`|  
|![Падение&#45;вниз по месту выбора нажата](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Поле выбора**|Граница|`Environment.DropDownMouseDownBorder`|  
|![Падение&#45;вниз по месту выбора нажата](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Поле выбора**|Разделитель|`Environment.DropDownButtonMouseDownSeparator`|  
|![Падение&#45;кнопку вниз нажатия](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Кнопка раскрывающегося списка**|Историческая справка|`Environment.DropDownButtonMouseDownBackground`|  
|![Падение&#45;кнопку вниз нажатия](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Кнопка раскрывающегося списка**|Передний план (глиф)|`Environment.DropDownMouseDownGlyph`|  
  
 **Отключен**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Падение&#45;вниз по месту выбора отключено](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Историческая справка|`Environment.DropDownDisabledBackground`|  
|![Падение&#45;вниз по месту выбора отключено](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Передний план (текст)|`Environment.DropDownDisabledText`|  
|![Падение&#45;вниз по месту выбора отключено](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Граница|`Environment.DropDownDisabledBorder`|  
|![Падение&#45;вниз по месту выбора отключено](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Разделитель|Без разделителя|  
|![Удаление&#45;кнопку отключена](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Историческая справка|Недоступно|  
|![Удаление&#45;кнопку отключена](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Передний план (глиф)|`Environment.DropDownDisabledGlyph`|  
  
##### <a name="split-button"></a>Разворачивающаяся кнопка  
 Для разворачивающихся кнопок используются многие имена токенов, определенные для других элементов управления панели команд, таких как кнопки, меню и текст панели команд. Все необходимые имена токенов для действий и кнопок раскрывающихся списков приводятся здесь еще раз для удобства. Раскрывающиеся списки разворачивающихся кнопок являются реализацией [Menus](../misc/shared-colors.md#BKMK_CommandMenus)панели команд.  
  
 ![Красная линия разворачивающейся кнопки](../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303-053_SplitButtonRedline")  
  
 Используйте:  
 при создании пользовательской разворачивающейся кнопки.  
  
Не используйте:  
- для других видов кнопок;  

- в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.  
  
  **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Разворачивающаяся кнопка](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Разворачивающаяся кнопка (по умолчанию)**|Историческая справка|None|  
|![Разворачивающаяся кнопка](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Разворачивающаяся кнопка (по умолчанию)**|Передний план (текст)|`Environment.CommandBarTextActive`|  
|![Разворачивающаяся кнопка](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Разворачивающаяся кнопка (по умолчанию)**|Передний план (глиф)|`Environment.CommandBarSplitButtonGlyph`|  
|![Разворачивающаяся кнопка](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Разворачивающаяся кнопка (по умолчанию)**|Граница|Недоступно|  
|![Разворачивающаяся кнопка](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Разворачивающаяся кнопка (по умолчанию)**|Разделитель|Недоступно|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Кнопка разделения на нависке](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Разворачивающаяся кнопка (при наведении указателя мыши)**|Историческая справка|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Кнопка разделения на нависке](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Разворачивающаяся кнопка (при наведении указателя мыши)**|Передний план (текст)|`Environment.CommandBarTextHover`|  
|![Кнопка разделения на нависке](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Разворачивающаяся кнопка (при наведении указателя мыши)**|Передний план (глиф)|`Environment.CommandBarSplitButtonMouseOverGlyph`|  
|![Кнопка разделения на нависке](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Разворачивающаяся кнопка (при наведении указателя мыши)**|Граница|`Environment.CommandBarBorder`|  
|![Кнопка разделения на нависке](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Разворачивающаяся кнопка (при наведении указателя мыши)**|Разделитель|`Environment.CommandBarSplitButtonSeparator`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Нажатие кнопки сплит](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Разворачивающаяся кнопка (активная)**|Историческая справка|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Нажатие кнопки сплит](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Разворачивающаяся кнопка (активная)**|Передний план (текст)|`Environment.CommandBarTextMouseDown`|  
|![Нажатие кнопки сплит](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Разворачивающаяся кнопка (активная)**|Передний план (глиф)|`Environment.CommandBarSplitButtonMouseDownGlyph`|  
|![Нажатие кнопки сплит](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Разворачивающаяся кнопка (активная)**|Граница|`Environment.CommandBarBorder`|  
|![Нажатие кнопки сплит](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Разворачивающаяся кнопка (активная)**|Разделитель|Недоступно|  
  
 **Отключен**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Кнопка сплит отключена](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Разворачивающаяся кнопка (неактивная)**|Историческая справка|Недоступно|  
|![Кнопка сплит отключена](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Разворачивающаяся кнопка (неактивная)**|Передний план (текст)|`Environment.ComboBoxItemTextInactive`|  
|![Кнопка сплит отключена](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Разворачивающаяся кнопка (неактивная)**|Передний план (глиф)|`Environment.CommandBarTextInactive`|  
|![Кнопка сплит отключена](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Разворачивающаяся кнопка (неактивная)**|Граница|Недоступно|  
|![Кнопка сплит отключена](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Разворачивающаяся кнопка (неактивная)**|Разделитель|Недоступно|  
  
##### <a name="more-options-and-overflow-buttons"></a>Кнопки "Дополнительно" и "Переполнение"  
 Кнопка "Дополнительно" используется, если группа панели команд может настраиваться путем добавления или удаления связанных кнопок. Кнопка "Переполнение" появляется, если панель команд усекается из-за отсутствия места по горизонтали. При ее нажатии открывается меню, содержащее кнопки, которые не поместились на панели команд. Цвета этих двух кнопок определяются одним и тем же набором имен токенов.  
  
 ![Красная линия дополнительных параметров](../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303-058_MoreOptionsRedline")  
  
 Используйте:  
 для пользовательских кнопок "Дополнительно" и "Переполнение".  
  
 Не используйте:  
 для кнопок, которые по своему предназначению отличаются от кнопки "Дополнительно" или "Переполнение".  
  
 **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Дополнительные параметры](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Дополнительные параметры**|Историческая справка|`Environment.CommandBarOptionsBackground`|  
|![Дополнительные параметры](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Дополнительные параметры**|Передний план (глиф)|`Environment.CommandBarOptionsGlyph`|  
|![Кнопка переполнения](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Переполнения**|Историческая справка|`Environment.CommandBarOptionsBackground`|  
|![Кнопка переполнения](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Переполнения**|Передний план (глиф)|`Environment.CommandBarOptionsGlyph`|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Дополнительные параметры при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Дополнительные параметры**|Историческая справка|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Дополнительные параметры при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Дополнительные параметры**|Передний план (глиф)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Переполнение при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Переполнения**|Историческая справка|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Переполнение при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Переполнения**|Передний план (глиф)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Активные дополнительные параметры](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Дополнительные параметры**|Историческая справка|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Активные дополнительные параметры](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Дополнительные параметры**|Передний план (глиф)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Активное переполнение](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Переполнения**|Историческая справка|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Активное переполнение](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Переполнения**|Передний план (глиф)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
### <a name="document-windows"></a>Окна документов  
 Воссоздавать окна документов не нужно, так как они предоставляются средой Visual Studio. Однако может потребоваться использовать цвета, применяемые в окнах документов, чтобы ваш пользовательский интерфейс был согласован с этой частью среды Visual Studio.  
  
 При использовании токенов цветов окна документов будьте внимательны: используйте их только для аналогичных элементов и всегда в парах. В противном случае результат может быть непредвиденным.  
  
#### <a name="document-window-frame"></a>Рамка окна документа  
 Окна документов могут быть закрепленными в интегрированной среде разработки или перемещаемыми как отдельные окна. Если окно документа является перемещаемым за пределами интегрированной среды разработки, оно по прежнему размещается в контейнере документа и имеет цвета фона, границы, текста и вкладок, которые совпадают с аналогичными цветами в интегрированной среде разработки. Однако документ размещается внутри рамки, которая имеет собственные цвета фона, границы и текста. Если в контейнере документа закреплены окна инструментов, они наследуют поведение и цвет вкладок от имен токенов окна документа.  
  
 ![Красная линия окна закрепленного документа](../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")  
  
 **Закрепленное окно документа**  
  
 ![Красная линия окна плавающего документа](../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")  
  
 **Перемещаемое окно документа**  
  
 Используйте:  
 при создании пользовательского интерфейса, соответствующего окну документа.  
  
 Не используйте:  
 для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
 **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|Документ: закрепленный или перемещаемый|Историческая справка|Зависит от типа документа|  
|Документ: закрепленный или перемещаемый|Передний план (текст)|Зависит от типа документа|  
|Документ: закрепленный или перемещаемый|Граница|`Environment.ToolWindowBorder`|  
|![Кадр с фокусом ввода](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Рамка: перемещаемая, с фокусом ввода**|Историческая справка|`Environment.ToolWindowFloatingFrame`|  
|![Кадр с фокусом ввода](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Рамка: перемещаемая, с фокусом ввода**|Передний план (текст)|`Environment.ToolWindowFloatingFrame`|  
|![Кадр с фокусом ввода](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Рамка: перемещаемая, с фокусом ввода**|Передний план (глиф)|`Environment.RaftedWindowButtonActiveGlyph`|  
|![Кадр с фокусом ввода](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Рамка: перемещаемая, с фокусом ввода**|Граница|`Environment.MainWindowActiveDefaultBorder`|  
|![Кадр с фокусом ввода](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Рамка: перемещаемая, с фокусом ввода**|Граница (глиф)|`Environment.RaftedWindowButtonActiveBorder`<br /><br /> Задается как прозрачная|  
|![Кадр без фокуса ввода](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Рамка: перемещаемая, без фокуса ввода**|Историческая справка|`Environment.ToolWindowFloatingFrameInactive`|  
|![Кадр без фокуса ввода](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Рамка: перемещаемая, без фокуса ввода**|Передний план (текст)|`Environment.ToolWindowFloatingFrameInactive`|  
|![Кадр без фокуса ввода](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Рамка: перемещаемая, без фокуса ввода**|Передний план (глиф)|`Environment.RaftedWindowButtonInactiveGlyph`|  
|![Кадр без фокуса ввода](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Рамка: перемещаемая, без фокуса ввода**|Граница|`Environment.MainWindowInactiveBorder`|  
|![Кадр без фокуса ввода](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Рамка: перемещаемая, без фокуса ввода**|Граница (глиф)|`Environment.RaftedWindowButtonInactiveBorder`<br /><br /> Задается как прозрачная|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Кадр с фокусом ввода при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Рамка: перемещаемая, с фокусом ввода**|Фон (глиф)|`Environment.RaftedWindowButtonHoverActive`|  
|![Кадр с фокусом ввода при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Рамка: перемещаемая, с фокусом ввода**|Передний план (глиф)|`Environment.RaftedWindowButtonHoverActiveGlyph`|  
|![Кадр с фокусом ввода при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Рамка: перемещаемая, с фокусом ввода**|Граница (глиф)|`Environment.RaftedWindowButtonHoverActiveBorder`|  
|![Кадр без фокуса ввода при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Рамка: перемещаемая, без фокуса ввода**|Фон (глиф)|`EnvironmentRaftedWindowButtonHoverInactive`|  
|![Кадр без фокуса ввода при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Рамка: перемещаемая, без фокуса ввода**|Передний план (глиф)|`Environment.RaftedWindowButtonHoverInactiveGlyph`|  
|![Кадр без фокуса ввода при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Рамка: перемещаемая, без фокуса ввода**|Граница (глиф)|`Environment.RaftedWindowButtonHoverInactiveBorder`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Активный кадр с фокусом ввода](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Рамка: перемещаемая, с фокусом ввода**|Фон (глиф)|`Environment.RaftedWindowButtonDown`|  
|![Активный кадр с фокусом ввода](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Рамка: перемещаемая, с фокусом ввода**|Передний план (глиф)|`Environment.RaftedWindowButtonDownGlyph`|  
|![Активный кадр с фокусом ввода](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Рамка: перемещаемая, с фокусом ввода**|Граница (глиф)|`Environment.RaftedWindowButtonDownBorder`|  
  
#### <a name="document-tabs"></a>Вкладки документов  
 Вкладки документов размещаются в канале вкладок и указывают, какие документы в настоящее время открыты, а также какой документ в настоящий момент выбран или активен. Окна инструментов также могут закрепляться в канале вкладок документов, если пользователь размещает их там. В этом случае для них используются те же цвета, что и для окон документов. Если вы создаете пользовательский интерфейс, цвета которого должны всегда соответствовать цветам окна документа (в том числе при обновлении темы или установке новых тем), то используйте ссылки на указанные ниже токены цветов.  
  
 ![Красная линия вкладки документов](../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303-072_DocumentTabRedline")  
  
 Используйте:  
 при создании пользовательского интерфейса, который должен соответствовать вкладкам документов и автоматически изменяться при обновлении тем или добавлении новых цветов темы.  
  
 Не используйте:  
 для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
##### <a name="open-document-tabs"></a>Вкладки открытых документов  
 Каждый открытый документ имеет вкладку в канале вкладок документов, на которой показано его имя. Документы могут быть либо выбраны, либо открыты в фоновом режиме. На их вкладках указываются перечисленные ниже состояния.  
  
- Выбранная вкладка представляет документ, который в настоящее время отображается в контейнере документа. Выбранная вкладка имеет границу документа, которая располагается по верхнему краю контейнера документа.  
  
- Фоновые вкладки представляют любые вкладки документов, которые не являются выбранной в настоящее время вкладкой. После нажатия они становятся выбранной вкладкой и приобретают все фоновые, пограничные и текстовые цвета из этих имен маркеров.  
  
  ![Красная линия открытой вкладки документов](../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")  
  
  Используйте:  
  при создании пользовательских вкладок документов.  
  
  Не используйте:  
  - для временных вкладок (вкладок предварительного просмотра);  
  
- для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
##### <a name="selected-tab"></a>Выбранная вкладка  
 **Focused**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Выбранная вкладка с фокусом ввода](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Выбранная вкладка документа, с фокусом ввода**|Историческая справка|`Environment.FileTabSelectedGradientTop`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Выбранная вкладка с фокусом ввода](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Выбранная вкладка документа, с фокусом ввода**|Передний план (текст)|`Environment.FileTabSelectedText`|  
|![Выбранная вкладка с фокусом ввода](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Выбранная вкладка документа, с фокусом ввода**|Граница|`Environment.FileTabSelectedBorder`<br /><br /> Цвет совпадает с цветом фона.|  
|![Выбранная вкладка с фокусом ввода](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Выбранная вкладка документа, с фокусом ввода**|Граница документа|`Environment.FileTabDocumentBorderBackground`|  
  
 **Без фокуса ввода**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Выбранная вкладка без фокуса ввода](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Выбранная вкладка документа, без фокуса ввода**|Историческая справка|`Environment.FileTabInactiveGradientTop`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Выбранная вкладка без фокуса ввода](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Выбранная вкладка документа, без фокуса ввода**|Передний план (текст)|`Environment.FileTabInactiveText`|  
|![Выбранная вкладка без фокуса ввода](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Выбранная вкладка документа, без фокуса ввода**|Граница|`Environment.FileTabInactiveBorder`<br /><br /> Цвет совпадает с цветом фона.|  
|![Выбранная вкладка без фокуса ввода](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Выбранная вкладка документа, без фокуса ввода**|Граница документа|`Environment.FileTabInactiveDocumentBorderBackground`|  
  
##### <a name="background-tab"></a>Вкладка фона  
 **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Цвет.категория|  
|---------------|-------------|--------------------------------|  
|![Вкладка фона](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Вкладка фона по умолчанию**|Историческая справка|`Environment.FileTabBackground`|  
|![Вкладка фона](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Вкладка фона по умолчанию**|Передний план (текст)|`Environment.FileTabText`|  
|![Вкладка фона](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Вкладка фона по умолчанию**|Граница|`Environment.FileTabBorder`<br /><br /> Цвет совпадает с цветом фона.|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Цвет.категория|  
|---------------|-------------|--------------------------------|  
|![Вкладка фона при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Вкладка фона при наведении курсора мыши**|Историческая справка|`Environment.FileTabHotGradientTop`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Вкладка фона при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Вкладка фона при наведении курсора мыши**|Передний план (текст)|`Environment.FileTabHotText`|  
|![Вкладка фона при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Вкладка фона при наведении курсора мыши**|Граница|`Environment.FileTabHotBorder`<br /><br /> Цвет совпадает с цветом фона.|  
  
##### <a name="preview-tab"></a>Вкладка предварительного просмотра  
 Вкладка предварительного просмотра отображается в правой части канала вкладок документов, когда пользователь щелкает элемент в окне инструментов обозревателя решений. Она служит для предварительного просмотра документа и дает пользователю возможность сохранять документ открытым в левой части канала вкладок документов. Одновременно может быть открыта только одна вкладка предварительного просмотра. Так же как открытые вкладки, вкладки предварительного просмотра имеют как фоновое, так и выбранное состояния и в активном состоянии могут получать фокус ввода и терять его.  
  
 ![Красная линия вкладки предварительного просмотра](../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303-078_PreviewTabRedline")  
  
 Используйте:  
 при создании временной области предварительного просмотра, если какой-либо элемент должен иметь цвет текущей вкладки предварительного просмотра.  
  
Не используйте:  
- для любого документа или вкладки, которая не является временной (не служит для предварительного просмотра);  

- для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
  **Выбранная вкладка предварительного просмотра с фокусом ввода**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Вкладка предварительного просмотра с фокусом ввода](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Вкладка предварительного просмотра с фокусом ввода**|Историческая справка|`Environment.FileTabProvisionalSelectedActive`|  
|![Вкладка предварительного просмотра с фокусом ввода](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Вкладка предварительного просмотра с фокусом ввода**|Передний план (текст)|`Environment.FileTabProvisionalSelectedActiveForeground`|  
|![Вкладка предварительного просмотра с фокусом ввода](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Вкладка предварительного просмотра с фокусом ввода**|Граница|`Environment.FileTabProvisionalSelectedActiveBorder`<br /><br /> Цвет совпадает с цветом фона.|  
|![Вкладка предварительного просмотра с фокусом ввода](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Вкладка предварительного просмотра с фокусом ввода**|Граница документа|`Environment.FileTabProvisionalSelectedActiveBorder`|  
  
 **Выбранная вкладка предварительного просмотра без фокуса ввода**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Вкладка предварительного просмотра без фокуса ввода](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Вкладка предварительного просмотра без фокуса ввода**|Историческая справка|`Environment.FileTabProvisionalSelectedInactive`|  
|![Вкладка предварительного просмотра без фокуса ввода](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Вкладка предварительного просмотра без фокуса ввода**|Передний план (текст)|`Environment.FileTabProvisionalSelectedInactiveForeground`|  
|![Вкладка предварительного просмотра без фокуса ввода](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Вкладка предварительного просмотра без фокуса ввода**|Граница|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
|![Вкладка предварительного просмотра без фокуса ввода](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Вкладка предварительного просмотра без фокуса ввода**|Граница документа|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
  
 **Фоновая вкладка предварительного просмотра: по умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Вкладка фона предварительного просмотра](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Фоновая вкладка предварительного просмотра**|Историческая справка|`Environment.FileTabProvisionalInactive`|  
|![Вкладка фона предварительного просмотра](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Фоновая вкладка предварительного просмотра**|Передний план (текст)|`Environment.FileTabProvisionalInactiveForeground`|  
|![Вкладка фона предварительного просмотра](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Фоновая вкладка предварительного просмотра**|Граница|`Environment.FileTabProvisionalInactiveBorder`<br /><br /> Цвет совпадает с цветом фона.|  
  
 **Фоновая вкладка предварительного просмотра: при наведении указателя**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Вкладка фона предварительного просмотра при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Фоновая вкладка предварительного просмотра при наведении указателя**|Историческая справка|`Environment.FileTabProvisionalHover`|  
|![Вкладка фона предварительного просмотра при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Фоновая вкладка предварительного просмотра при наведении указателя**|Передний план (текст)|`Environment.FileTabProvisionalHoverForeground`|  
|![Вкладка фона предварительного просмотра при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Фоновая вкладка предварительного просмотра при наведении указателя**|Граница|`Environment.FileTabProvisionalHoverBorder`<br /><br /> Цвет совпадает с цветом фона.|  
  
##### <a name="document-overflow-button"></a>Кнопка переполнения документа  
 Кнопка переполнения документа присутствует, если открыт один или несколько документов, вне зависимости от того, имеется ли в текущей конфигурации пространство по вертикали для размещения всех вкладок документов. В раскрывающемся меню переполнения документа, к которому применяются цвета **CommandBarMenu** (см. раздел [Menus](../misc/shared-colors.md#BKMK_CommandMenus)), приводится список всех открытых документов, как видимых, так и скрытых. Глиф переполнения меняется в зависимости от того, отображаются ли все открытые документы в канале вкладок.  
  
 ![Красная линия переполнения](../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303-083_OverflowRedline")  
  
Используйте:  
при создании пользовательской кнопки переполнения документа.  

Не используйте:  
- для пользовательского интерфейса, отличного от кнопки переполнения;  

- для кнопок переполнения панели команд.  
  
  **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Переполнения](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Кнопка переполнения документа**|Историческая справка|`Environment.DocWellOverflowButtonBackground`|  
|![Переполнения](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Кнопка переполнения документа**|Передний план (глиф)|`Environment.DocWellOverflowButtonGlyph`|  
|![Переполнения](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Кнопка переполнения документа**|Граница|Недоступно|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Переполнение при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Кнопка переполнения документа при наведении указателя**|Историческая справка|`Environment.DocWellOverflowButtonMouseOverBackground`|  
|![Переполнение при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Кнопка переполнения документа при наведении указателя**|Передний план (глиф)|`Environment.DocWellOverflowButtonMouseOverGlyph`|  
|![Переполнение при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Кнопка переполнения документа при наведении указателя**|Граница|`Environment.DocWellOverflowButtonMouseOverBorder`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Активное переполнение](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Активная кнопка переполнения документа**|Историческая справка|`Environment.DocWellOverflowButtonMouseDownBackground`|  
|![Активное переполнение](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Активная кнопка переполнения документа**|Передний план (глиф)|`Environment.DocWellOverflowButtonMouseDownGlyph`|  
|![Активное переполнение](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Активная кнопка переполнения документа**|Граница|`Environment.DocWellOverflowButtonMouseDownBorder`|  
  
### <a name="tool-windows"></a>Окна инструментов  
 Воссоздавать окна инструментов не нужно, так как они предоставляются средой Visual Studio. Однако может потребоваться использовать цвета, применяемые в окнах инструментов, чтобы ваш пользовательский интерфейс был согласован с этой частью среды Visual Studio.  
  
 ![Красная линия окна инструментов](../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303-087_ToolWindowRedline")  
  
 Используйте:  
 при создании пользовательского интерфейса, соответствующего окнам инструментов.  
  
 Не используйте:  
 для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
#### <a name="tool-window-frame"></a>Рамка окна инструментов  
 Окна инструментов в Visual Studio используются для множества различных задач и могут иметь одно из нескольких состояний. Если окно инструментов открыто, оно может быть назначено одной из четырех сторон области документа. Окна инструментов также могут перемещаться за пределы интегрированной среды документов, что позволяет размещать их в любом месте экрана. Перемещаемые окна всегда находятся поверх интегрированной среды разработки. Наконец, окна инструментов могут закрепляться как окна документов и отображаться в виде вкладок в контейнере документа. К окнам инструментов, закрепленным как окна документов, частично применяются имена токенов окна документа.  
  
 ![Красная линия кадра окна инструментов](../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")  
  
 Используйте:  
 при создании пользовательского интерфейса, соответствующего окнам инструментов.  
  
 Не используйте:  
 для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
 **Закрепленное**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Закрепленное окно инструментов](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Историческая справка|`Environment.ToolWindowBackground`|  
|![Закрепленное окно инструментов](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Граница|`Environment.ToolWindowBorder`|  
  
 **Перемещаемое: с фокусом ввода**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Окно инструментов в фокусе](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Историческая справка|`Environment.ToolWindowBackground`|  
|![Окно инструментов в фокусе](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Граница|`Environment.MainWindowActiveDefaultBorder`|  
  
 **Перемещаемое: без фокуса ввода**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Окно инструментов не в фокусе](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Историческая справка|`Environment.ToolWindowBackground`|  
|![Окно инструментов не в фокусе](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Граница|`Environment.MainWindowInactiveBorder`|  
  
#### <a name="tool-window-title-bar"></a>Заголовок окна инструментов  
 Граница заголовка окна является, по сути, не границей, а толстой линией по верхнему краю заголовка. Она не имеет имени токена для состояния без фокуса ввода.  
  
 ![Красная линия панели заголовка окна инструментов](../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")  
  
 Используйте:  
 при создании пользовательского интерфейса, соответствующего окнам инструментов.  
  
 Не используйте:  
 для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
 **Focused**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Панель заголовка в фокусе](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Заголовок окна с фокусом ввода**|Историческая справка|`Environment.TitleBarActiveGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Панель заголовка в фокусе](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Заголовок окна с фокусом ввода**|Передний план (текст)|`Environment.TitleBarActiveText`|  
|![Панель заголовка в фокусе](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Заголовок окна с фокусом ввода**|Граница|`Environment.TitleBarActiveBorder`<br /><br /> Цвет совпадает с цветом фона.|  
|![Панель заголовка в фокусе](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Заголовок окна с фокусом ввода**|Маркер перетаскивания|`Environment.TitleBarDragHandleActive`|  
  
 **Без фокуса ввода**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Панель заголовка без фокуса ввода](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Заголовок окна без фокуса ввода**|Историческая справка|`Environment.TitleBarInactiveGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Панель заголовка без фокуса ввода](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Заголовок окна без фокуса ввода**|Передний план (текст)|`Environment.TitleBarInactiveText`|  
|![Панель заголовка без фокуса ввода](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Заголовок окна без фокуса ввода**|Граница|Недоступно|  
|![Панель заголовка без фокуса ввода](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Заголовок окна без фокуса ввода**|Маркер перетаскивания|`Environment.TitleBarDragHandle`|  
  
##### <a name="title-bar-buttons"></a>Кнопки в заголовке окна  
 ![Красная линия кнопки панели заголовка](../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")  
  
 Используйте:  
 для кнопок в пользовательском интерфейсе, для которых используются токены цветов, связанные с заголовками окон инструментов.  
  
Не используйте:  
- для кнопок, отображаемых в других местах;  

- в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.  
  
  **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Кнопка панели заголовка с фокусом ввода](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Focused**|Историческая справка|Недоступно|  
|![Кнопка панели заголовка с фокусом ввода](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Focused**|Передний план (глиф)|`Environment.ToolWindowButtonActiveGlyph`|  
|![Кнопка панели заголовка с фокусом ввода](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Focused**|Граница|Недоступно|  
|![Кнопка панели заголовка без фокуса ввода](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Без фокуса ввода**|Историческая справка|Недоступно|  
|![Кнопка панели заголовка без фокуса ввода](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Без фокуса ввода**|Передний план (глиф)|`Environment.ToolWindowButtonInactiveGlyph`|  
|![Кнопка панели заголовка без фокуса ввода](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Без фокуса ввода**|Граница|Недоступно|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Кнопка панели заголовка с фокусом ввода при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Focused**|Историческая справка|`Environment.ToolWindowButtonHoverActive`|  
|![Кнопка панели заголовка с фокусом ввода при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Focused**|Передний план (глиф)|`Environment.ToolWindowButtonHoverActiveGlyph`|  
|![Кнопка панели заголовка с фокусом ввода при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Focused**|Граница|`Environment.ToolWindowButtonHoverActiveBorder`|  
|![Кнопка панели заголовка без фокуса ввода при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Без фокуса ввода**|Историческая справка|`Environment.ToolWindowButtonHoverInactive`|  
|![Кнопка панели заголовка без фокуса ввода при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Без фокуса ввода**|Передний план (глиф)|`Environment.ToolWindowButtonHoverInactiveGlyph`|  
|![Кнопка панели заголовка без фокуса ввода при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Без фокуса ввода**|Граница|`Environment.ToolWindowButtonHoverInactiveBorder`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Активная кнопка панели заголовка с фокусом ввода](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Focused**|Историческая справка|`Environment.ToolWindowButtonDown`|  
|![Активная кнопка панели заголовка с фокусом ввода](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Focused**|Передний план (глиф)|`Environment.ToolWindowButtonDownActiveGlyph`|  
|![Активная кнопка панели заголовка с фокусом ввода](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Focused**|Граница|`Environment.ToolWindowButtonDownBorder`|  
|![Активная кнопка панели заголовка без фокуса ввода](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Без фокуса ввода**|Историческая справка|`Environment.ToolWindowButtonDown`|  
|![Активная кнопка панели заголовка без фокуса ввода](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Без фокуса ввода**|Передний план (глиф)|`Environment.ToolWindowButtonDownInactiveGlyph`|  
|![Активная кнопка панели заголовка без фокуса ввода](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Без фокуса ввода**|Граница|`Environment.ToolWindowButtonDownBorder`|  
  
#### <a name="tool-window-tabs"></a>Вкладки окна инструментов  
 ![Красная линия вкладки окна инструментов](../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303-102_ToolWindowTabRedline")  
  
 Используйте:  
 при создании пользовательского интерфейса, соответствующего окнам инструментов.  
  
 Не используйте:  
 для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
 **Выбранная вкладка**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Вкладка окна инструментов с фокусом ввода](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Выбранная вкладка окна инструментов с фокусом ввода**|Историческая справка|`Environment.ToolWindowTabSelectedTab`|  
|![Вкладка окна инструментов с фокусом ввода](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Выбранная вкладка окна инструментов с фокусом ввода**|Передний план (текст)|`Environment.ToolWindowTabSelectedActiveText`|  
|![Вкладка окна инструментов с фокусом ввода](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Выбранная вкладка окна инструментов с фокусом ввода**|Граница|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Цвет совпадает с цветом фона.|  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Вкладка окна инструментов без фокуса ввода](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Выбранная вкладка окна инструментов без фокуса ввода**|Историческая справка|`Environment.ToolWindowTabSelectedTab`|  
|![Вкладка окна инструментов без фокуса ввода](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Выбранная вкладка окна инструментов без фокуса ввода**|Передний план (текст)|`Environment.ToolWindowTabSelectedText`|  
|![Вкладка окна инструментов без фокуса ввода](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Выбранная вкладка окна инструментов без фокуса ввода**|Граница|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Цвет совпадает с цветом фона.|  
  
 **Вкладка фона**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Вкладка фона окна инструментов](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Фоновая вкладка окна инструментов**|Историческая справка|`Environment.ToolWindowTabGradientBegin`<br /><br /> Ограничения градиента устанавливаются в Visual Studio 2013 в то же значение цвета.<br /><br /> `Environment.ToolWindowTabGradientEnd`<br /><br /> Ограничения градиента устанавливаются в Visual Studio 2013 в то же значение цвета.|  
|![Вкладка фона окна инструментов](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Фоновая вкладка окна инструментов**|Передний план (текст)|`Environment.ToolWindowTabText`|  
|![Вкладка фона окна инструментов](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Фоновая вкладка окна инструментов**|Граница|`Environment.ToolWindowTabBorder`|  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Вкладка фона окна инструментов при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Фоновая вкладка окна инструментов при наведении указателя**|Историческая справка|`Environment.ToolWindowTabMouseOverBackgroundBegin`<br /><br /> Ограничения градиента устанавливаются в Visual Studio 2013 в то же значение цвета.<br /><br /> `Environment.ToolWindowTabMouseOverBackgroundEnd`<br /><br /> Ограничения градиента устанавливаются в Visual Studio 2013 в то же значение цвета.|  
|![Вкладка фона окна инструментов при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Фоновая вкладка окна инструментов при наведении указателя**|Передний план (текст)|`Environment.ToolWindowTabMouseOverText`|  
|![Вкладка фона окна инструментов при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Фоновая вкладка окна инструментов при наведении указателя**|Граница|`Environment.ToolWindowTabMouseOverBorder`<br /><br /> Цвет совпадает с цветом фона.|  
  
#### <a name="auto-hide-tabs"></a>Автоматически скрываемые вкладки  
 ![Авто&#45;скрыть красную линию](../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303-107_AutoHideRedline")  
  
 Используйте:  
 при создании пользовательского интерфейса, соответствующего автоматически скрываемым вкладкам окна инструментов.  
  
 Не используйте:  
 для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
 **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Авто&#45;скрыть вкладку](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Автоматически скрываемая вкладка по умолчанию**|Историческая справка|`Environment.AutoHideTabBackgroundBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Авто&#45;скрыть вкладку](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Автоматически скрываемая вкладка по умолчанию**|Передний план (текст)|`Environment.AutoHideTabText`|  
|![Авто&#45;скрыть вкладку](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Автоматически скрываемая вкладка по умолчанию**|Граница|`Environment.AutoHideTabBorder`|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Авто&#45;скрыть вкладку на нависшие](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Вкладка автоматического скрытия при наведении курсора мыши**|Историческая справка|`Environment.AutoHideTabMouseOverBackgroundBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Авто&#45;скрыть вкладку на нависшие](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Вкладка автоматического скрытия при наведении курсора мыши**|Передний план (текст)|`Environment.AutoHideTabMouseOverText`|  
|![Авто&#45;скрыть вкладку на нависшие](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Вкладка автоматического скрытия при наведении курсора мыши**|Граница|`Environment.AutoHideTabMouseOverBorder`|  
  
### <a name="common-shared-controls"></a>Стандартные общие элементы управления  
 При использовании в компоненте стандартной панели команд Visual Studio вы имеете доступ к оформленным элементам управления оболочки. Изменять шаблон этих стандартных элементов управления не следует. Однако если вам нужно создать пользовательскую панель команд, вам также может потребоваться создать пользовательские элементы управления. В этом случае используйте правильные имена токенов для каждого из указанных ниже элементов управления, чтобы ваш пользовательский интерфейс был согласован с остальной средой Visual Studio.  
  
#### <a name="search-box"></a>Поле поиска  
 По возможности используйте стандартный элемент управления поиском, предоставляемый средой Visual Studio. Цвета поля поиска находятся в категории SearchControl в файле **ShellColors.pkgdef** , который содержит имена токенов для поля ввода, управляющей кнопки, кнопки раскрывающегося списка и раскрывающегося меню.  
  
 Поле поиска может находиться в одном из нескольких состояний. Некоторые из них взаимоисключающие.  
  
- "С фокусом ввода" или "без фокуса ввода" указывает на то, находится ли курсор в текстовом поле.  
  
- "Активно" или "неактивно" указывает на то, ввел ли пользователь запрос в текстовом поле.  
  
- "При наведении указателя" означает, что пользователь навел указатель мыши на поле поиска (это состояние переопределяет все остальные).  
  
- "Отключено" означает, что функция поиска в текущем контексте отключена.  
  
  ![Красная линия окна поиска](../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303-110_SearchBoxRedline")  
  
  Используйте:  
  при разработке пользовательского поля поиска.  
  
  Не используйте:  
  - для любого элемента, не являющегося полем поиска;  
  
- для любого элемента, который не должен всегда соответствовать пользовательскому интерфейсу поля поиска.  
  
  **Focused**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Поле ввода окна поиска с фокусом ввода](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Поле ввода**|Историческая справка|`SearchControl.FocusedBackground`|  
|![Поле ввода окна поиска с фокусом ввода](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Поле ввода**|Передний план (текст)|`SearchControl.FocusedBackground`|  
|![Поле ввода окна поиска с фокусом ввода](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Поле ввода**|Граница|`SearchControl.FocusedBorder`|  
|![Поле ввода окна поиска с фокусом ввода](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Поле ввода**|Разделитель|`SearchControl.FocusedDropDownSeparator`|  
|![Кнопка поиска с фокусом ввода](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Кнопка действия**|Историческая справка|None|  
|![Кнопка поиска с фокусом ввода](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Кнопка действия**|Передний план (глиф поиска)|`SearchControl.SearchGlyph`|  
|![Кнопка поиска с фокусом ввода](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Кнопка действия**|Передний план (глиф остановки)|`SearchControl.StopGlyph`|  
|![Кнопка поиска с фокусом ввода](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Кнопка действия**|Передний план (глиф очистки)|`SearchControl.ClearGlyph`|  
|![Кнопка поиска с фокусом ввода](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Кнопка действия**|Граница|Недоступно|  
|![Поиск падение&#45;вниз кнопку сосредоточены](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Кнопка раскрывающегося списка**|Историческая справка|`SearchControl.FocusedDropDownButton`|  
|![Поиск падение&#45;вниз кнопку сосредоточены](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Кнопка раскрывающегося списка**|Передний план (глиф)|`SearchControl.FocusedDropDownButtonGlyph`|  
|![Поиск падение&#45;вниз кнопку сосредоточены](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Кнопка раскрывающегося списка**|Граница|`SearchControl.FocusedDropDownButtonBorder`|  
  
 **Без фокуса ввода**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Поле ввода окна поиска без фокуса ввода](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Активное поле ввода**|Историческая справка|`SearchControl.SearchActiveBackground`|  
|![Поле ввода окна поиска без фокуса ввода](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Активное поле ввода**|Передний план (текст)|`SearchControl.SearchActiveBackground`|  
|![Поле ввода окна поиска без фокуса ввода](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Активное поле ввода**|Граница|`SearchControl.UnfocusedBorder`|  
|![Поле ввода окна поиска без фокуса ввода](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Активное поле ввода**|Разделитель|`SearchControl.DropDownSeparator`|  
|![Неактивное поле ввода окна поиска без фокуса ввода](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Неактивное поле ввода**|Историческая справка|`SearchControl.Unfocused`|  
|![Неактивное поле ввода окна поиска без фокуса ввода](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Неактивное поле ввода**|Передний план (текст)|`SearchControl.Unfocused`|  
|![Неактивное поле ввода окна поиска без фокуса ввода](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Неактивное поле ввода**|Граница|`SearchControl.UnfocusedBorder`|  
|![Неактивное поле ввода окна поиска без фокуса ввода](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Неактивное поле ввода**|Разделитель|`SearchControl.DropDownSeparator`|  
|![Кнопка поиска без фокуса ввода](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Кнопка действия**|Историческая справка|Недоступно|  
|![Кнопка поиска без фокуса ввода](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Кнопка действия**|Передний план (глиф поиска)|`SearchControl.SearchGlyph`|  
|![Кнопка поиска без фокуса ввода](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Кнопка действия**|Передний план (глиф остановки)|`SearchControl.StopGlyph`|  
|![Кнопка поиска без фокуса ввода](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Кнопка действия**|Передний план (глиф очистки)|`SearchControl.ClearGlyph`|  
|![Кнопка поиска без фокуса ввода](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Кнопка действия**|Граница|Недоступно|  
|![Поиск падение&#45;вниз кнопку нецеленаправленной](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Кнопка раскрывающегося списка**|Историческая справка|`SearchControl.UnfocusedDropDownButton`|  
|![Поиск падение&#45;вниз кнопку нецеленаправленной](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Кнопка раскрывающегося списка**|Передний план (глиф)|`SearchControl.UnfocusedDropDownButtonGlyph`|  
|![Поиск падение&#45;вниз кнопку нецеленаправленной](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Кнопка раскрывающегося списка**|Граница|`SearchControl.UnfocusedDropDownButtonBorder`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Активная кнопка поиска](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Кнопка действия**|Историческая справка|`SearchControl.ActionButtonMouseDown`|  
|![Активная кнопка поиска](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Кнопка действия**|Передний план (глиф)|`SearchControl.ActionButtonMouseDownGlyph`|  
|![Активная кнопка поиска](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Кнопка действия**|Граница|`SearchControl.ActionButtonMouseDownBorder`|  
|![Поиск падение&#45;кнопку вниз нажатия](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Кнопка раскрывающегося списка**|Историческая справка|`SearchControl.MouseDownDropDownButton`|  
|![Поиск падение&#45;кнопку вниз нажатия](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Кнопка раскрывающегося списка**|Передний план (глиф)|`SearchControl.MouseDownDropDownButtonGlyph`|  
|![Поиск падение&#45;кнопку вниз нажатия](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Кнопка раскрывающегося списка**|Граница|`SearchControl.MouseDownDropDownButtonBorder`|  
  
 **Выделено (только текст)**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Выделение поля ввода окна поиска](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Поле ввода с выделенным текстом**|Историческая справка|`SearchControl.Selection`|  
|![Выделение поля ввода окна поиска](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Поле ввода с выделенным текстом**|Передний план (текст)|`SearchControl.FocusedBackground`|  
|![Выделение поля ввода окна поиска](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Поле ввода с выделенным текстом**|Граница|None|  
|![Выделение поля ввода окна поиска](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Поле ввода с выделенным текстом**|Разделитель|`SearchControl.FocusedDropDownSeparator`|  
  
 **Отключен**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Неактивное поле ввода окна поиска](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Поле ввода**|Историческая справка|`SearchControl.Disabled`|  
|![Неактивное поле ввода окна поиска](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Поле ввода**|Передний план (текст)|`SearchControl.Disabled`|  
|![Неактивное поле ввода окна поиска](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Поле ввода**|Граница|`SearchControl.DisabledBorder`|  
|![Неактивное поле ввода окна поиска](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Поле ввода**|Разделитель|`SearchControl.DropDownSeparator`|  
|![Неактивная кнопка поиска](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Кнопка действия**|Историческая справка|None|  
|![Неактивная кнопка поиска](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Кнопка действия**|Передний план (глиф)|`SearchControl.ActionButtonDisabledGlyph`|  
|![Неактивная кнопка поиска](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Кнопка действия**|Граница|None|  
|![Поиск падение&#45;вниз кнопка отключена](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Кнопка раскрывающегося списка**|Историческая справка|None|  
|![Поиск падение&#45;вниз кнопка отключена](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Кнопка раскрывающегося списка**|Передний план (глиф)|`SearchControl.DisabledDownButtonGlyph`|  
|![Поиск падение&#45;вниз кнопка отключена](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Кнопка раскрывающегося списка**|Граница|None|  
  
##### <a name="search-drop-down-lists"></a>Раскрывающиеся списки поиска  
 Раскрывающиеся меню в поле поиска могут быть немного более сложными, чем другие раскрывающиеся меню в Visual Studio. Разделы "предлагаемые запросы поиска" и "параметры поиска" могут присутствовать в меню вместе или по отдельности. Каждый из них имеет особые цвета. Если имеются оба этих раздела, они разделяются линией, а все раскрывающееся меню окружено границей.  
  
 ![Поиск падение&#45;вниз красная линия](../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303-124_SearchDropdownRedline")  
  
Используйте:  
- при создании пользовательского раскрывающегося списка поиска;  

- правильные имена токенов для соответствующих компонентов списка.  

Не используйте:  
- для раскрывающихся списков, которые используются в других контекстах;  

- в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.  
  
  **По умолчанию (нет других состояний)**  
  
|Элемент|Имя токена: Category.color|  
|-------------|--------------------------------|  
|Граница|`SearchControl.PopupBorder`|  
|Разделитель|`SearchControl.PopupSectionHeaderSeparator`|  
|Shadow|`Environment.DropShadowBackground`|  
  
 **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Предлагаемый поиск](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Предлагаемые запросы поиска**|Историческая справка|`SearchControl.PopupItemsListBackgroundGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Предлагаемый поиск](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Предлагаемые запросы поиска**|Передний план (текст)|`SearchControl.PopupItemText`|  
|![Флажок поиска](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Параметры поиска (флажок)**|Историческая справка|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Варианты поиска](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Параметры поиска (ссылка)**|Историческая справка|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Флажок поиска](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Параметры поиска (флажок)**|Передний план (текст флажка)|`SearchControl.PopupCheckboxText`|  
|![Варианты поиска](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Параметры поиска (ссылка)**|Передний план (текст флажка)|`SearchControl.PopupCheckboxText`|  
|![Флажок поиска](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Параметры поиска (флажок)**|Передний план (текст ссылки)|`SearchControl.PopupButtonText`|  
|![Варианты поиска](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Параметры поиска (ссылка)**|Передний план (текст ссылки)|`SearchControl.PopupButtonText`|  
|![Флажок поиска](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Параметры поиска (флажок)**|Фон заголовка|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Варианты поиска](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Параметры поиска (ссылка)**|Фон заголовка|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Флажок поиска](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Параметры поиска (флажок)**|Передний план (текст заголовка)|`SearchControl.PopupSectionHeaderText`|  
|![Варианты поиска](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Параметры поиска (ссылка)**|Передний план (текст заголовка)|`SearchControl.PopupSectionHeaderText`|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Предлагаемый поиск при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Предлагаемые запросы поиска**|Историческая справка|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Предлагаемый поиск при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Предлагаемые запросы поиска**|Передний план (текст)|`SearchControl.PopupMouseOverItemText`|  
|![Предлагаемый поиск при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Предлагаемые запросы поиска**|Граница|`SearchControl.PopupControlMouseOverBorder`|  
|![Флажок поиска при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Предлагаемые запросы поиска (флажок)**|Историческая справка|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Параметры поиска при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Варианты поиска**|Историческая справка|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Флажок поиска при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Предлагаемые запросы поиска (флажок)**|Передний план (текст флажка)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Параметры поиска при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Варианты поиска**|Передний план (текст флажка)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Флажок поиска при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Предлагаемые запросы поиска (флажок)**|Передний план (текст ссылки)|`SearchControl.PopupButtonMouseDownText`|  
|![Параметры поиска при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Варианты поиска**|Передний план (текст ссылки)|`SearchControl.PopupButtonMouseDownText`|  
|![Флажок поиска при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Предлагаемые запросы поиска (флажок)**|Граница|`SearchControl.PopupControlMouseOverBorder`|  
|![Параметры поиска при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Варианты поиска**|Граница|`SearchControl.PopupControlMouseOverBorder`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Активный предлагаемый поиск](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Предлагаемые запросы поиска (флажок)**|Фон флажка|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Активные параметры поиска](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Варианты поиска**|Фон флажка|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Активный предлагаемый поиск](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Предлагаемые запросы поиска (флажок)**|Фон флажка|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Активные параметры поиска](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Варианты поиска**|Фон флажка|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Активный предлагаемый поиск](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Предлагаемые запросы поиска (флажок)**|Передний план (текст флажка)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Активные параметры поиска](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Варианты поиска**|Передний план (текст флажка)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Активный предлагаемый поиск](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Предлагаемые запросы поиска (флажок)**|Фон ссылки|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Активные параметры поиска](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Варианты поиска**|Фон ссылки|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.|  
|![Активный предлагаемый поиск](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Предлагаемые запросы поиска (флажок)**|Передний план (текст ссылки)|`SearchControl.PopupButtonMouseDownText`|  
|![Активные параметры поиска](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Варианты поиска**|Передний план (текст ссылки)|`SearchControl.PopupButtonMouseDownText`|  
  
#### <a name="hyperlink"></a>Hyperlink  
 Гиперссылка — это один из элементов управления, для которого нет пары цветов переднего плана и фона. Во всех случаях используйте основной цвет гиперссылки, который будет правильно отображаться на темном, сером и белом фоне. Если вы не используете токен цвета для элемента управления "гиперссылка", то будет применяться системный цвет по умолчанию для состояния "активно", то есть гиперссылка будет мигать красным. Это означает, что для элемента управления используется неправильный токен цвета среды.  
  
 ![Красная линия гиперссылки](../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303-133_HyperlinkRedline")  
  
 Используйте:  
 если нужно создать пользовательскую гиперссылку.  
  
 Не используйте:  
 для любого элемента, не являющегося гиперссылкой.  
  
 **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Гиперссылка по умолчанию](../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303-134_Hyperlink")|Передний план (текст)|`Environment.PanelHyperlink`|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Гиперссылка при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303-135_HyperlinkHover")|Передний план (текст)|`Environment.PanelHyperlinkHover`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Активная гиперссылка](../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303-136_HyperlinkPressed")|Передний план (текст)|`Environment.PanelHyperlinkPressed`|  
  
 **Отключен**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Неактивная гиперссылка](../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303-137_HyperlinkDisabled")|Передний план (текст)|`Environment.PanelHyperlinkDisabled`|  
  
#### <a name="infobar"></a>Информационная панель  
 Информационные панели служат для предоставления дополнительной информации о данном контексте и всегда отображаются в верхней части окна документа или окна инструментов.  
  
 ![Красная линия информационной панели](../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303-138_InfobarRedline")  
  
 Используйте:  
 при создании пользовательских информационных панелей.  
  
 Не используйте:  
 для элементов пользовательского интерфейса, которые не похожи на информационную панель.  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Информационная панель](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Информационная панель**|Историческая справка|`Environment.InfoBackground`|  
|![Информационная панель](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Информационная панель**|Передний план (текст)|`Environment.InfoText`|  
|![Информационная панель](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Информационная панель**|Граница|`Environment.ToolWindowBorder`|  
  
#### <a name="scroll-bar"></a>Полоса прокрутки  
 Полосы прокрутки оформляются средой Visual Studio, и применять к ним темы не нужно. Тем не менее, вы можете решить, что вы хотите использовать цвета, используемые в барах прокрутки, так что ваш uI всегда отображается в соответствии с этой частью среды Visual Studio.  
  
 ![Красная линия полосы прокрутки](../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303-140_ScrollbarRedline")  
  
 Используйте:  
 при создании пользовательского интерфейса, который должен соответствовать полосам прокрутки Visual Studio.  
  
 Не используйте:  
 для каких-либо элементов, которые не должны всегда соответствовать пользовательскому интерфейсу полос прокрутки.  
  
 **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Прокрутка бар](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Scrollbar**|Полоса прокрутки|`Environment.ScrollBarBackground`|  
|![Прокрутка бар](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Scrollbar**|Передний план (бегунок)|`Environment.ScrollBarThumbBackground`|  
|![Стрелки полосы прокрутки](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Стрелка прокрутки**|Историческая справка|`Environment.ScrollBarArrowBackground`<br /><br /> Цвет совпадает с цветом полосы прокрутки.|  
|![Стрелки полосы прокрутки](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Стрелка прокрутки**|Передний план (глиф)|`Environment.ScrollBarArrowGlyph`|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Полоса прокрутки при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Scrollbar**|Полоса прокрутки|`Environment.ScrollBarBackground`|  
|![Полоса прокрутки при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Scrollbar**|Передний план (бегунок)|`Environment.ScrollBarThumbMouseOverBackground`|  
|![Стрелки полосы прокрутки при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Стрелка прокрутки**|Историческая справка|`Environment.ScrollBarArrowMouseOverBackground`<br /><br /> Цвет совпадает с цветом полосы прокрутки.|  
|![Стрелки полосы прокрутки при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Стрелка прокрутки**|Передний план (глиф)|`Environment.ScrollBarArrowGlyphMouseOver`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Активная полоса прокрутки](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Scrollbar**|Полоса прокрутки|`Environment.ScrollBarBackground`|  
|![Активная полоса прокрутки](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Scrollbar**|Передний план (бегунок)|`Environment.ScrollBarThumbPressedBackground`|  
|![Активные стрелки полосы прокрутки](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Стрелка прокрутки**|Историческая справка|`Environment.ScrollBarArrowPressedBackground`<br /><br /> Цвет совпадает с цветом полосы прокрутки.|  
|![Активные стрелки полосы прокрутки](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Стрелка прокрутки**|Передний план (глиф)|`Environment.ScrollBarArrowGlyphPressed`|  
  
#### <a name="tree-view"></a><a name="BKMK_TreeView"></a>Вид дерева  
 В некоторых окнах инструментов, включая обозреватель решений, обозреватель сервера и представление классов, реализована иерархическая организационная схема, цвета которой определяются названиями цветов в категории TreeView. Все элементы в иерархическом представлении имеют цвета фона и текста. Элементы с вложенными дочерними элементами также имеют глифы, которые указывают на то, является ли элемент свернутым или развернутым.  
  
 ![Красная линия представления в виде дерева](../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303-147_TreeViewRedline")  
  
 Используйте:  
 если необходимо реализовать иерархическое представление.  
  
Не используйте:  
- для каких-либо элементов, отличных от иерархического представления;  

- в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.  
  
  **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Вид дерева](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Историческая справка|`TreeView.Background`|  
|![Вид дерева](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Передний план (текст)|`TreeView.Background`|  
|![Вид дерева](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Передний план (глиф)|`TreeView.Glyph`|  
|![Вид дерева](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Граница|None|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Представление в виде дерева при наведении указателя мыши](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Историческая справка|`TreeView.Background`|  
|![Представление в виде дерева при наведении указателя мыши](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Передний план (текст)|`TreeView.Background`|  
|![Представление в виде дерева при наведении указателя мыши](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Передний план (глиф)|`TreeView.GlyphMouseOver`|  
|![Представление в виде дерева при наведении указателя мыши](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Граница|None|  
  
 **Перетаскивание**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Перетаскивание иерархического представления](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Историческая справка|`TreeView.DragOverItem`|  
|![Перетаскивание иерархического представления](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Передний план (текст)|`TreeView.DragOverItem`|  
|![Перетаскивание иерархического представления](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Передний план (глиф)|`TreeView.DragOverItemGlyph`|  
|![Перетаскивание иерархического представления](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Граница|None|  
  
 **Выбрано**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Иерархическое представление в фокусе](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|Историческая справка|`TreeView.SelectedItemActive`|  
|![Иерархическое представление в фокусе](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|Передний план (текст)|`TreeView.SelectedItemActive`|  
|![Иерархическое представление в фокусе](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|Передний план (глиф)|`TreeView.SelectedItemActiveGlyph`|  
|![Иерархическое представление в фокусе](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|Граница|`TreeView.FocusVisualBorder`|  
|![Представление в виде дерева в фокусе](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Без фокуса ввода**|Историческая справка|`TreeView.SelectedItemInactive`|  
|![Представление в виде дерева в фокусе](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Без фокуса ввода**|Передний план (текст)|`TreeView.SelectedItemInactive`|  
|![Представление в виде дерева в фокусе](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Без фокуса ввода**|Передний план (глиф)|`TreeView.SelectedItemInactiveGlyph`|  
|![Представление в виде дерева в фокусе](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Без фокуса ввода**|Граница|None|  
  
 **Наведение указателя на выделенный элемент**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Представление в виде дерева в фокусе при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|Историческая справка|`TreeView.SelectedItemActive`|  
|![Представление в виде дерева в фокусе при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|Передний план (текст)|`TreeView.SelectedItemActive`|  
|![Представление в виде дерева в фокусе при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|Передний план (глиф)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Представление в виде дерева в фокусе при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|Граница|Нет`TreeView.FocusVisualBorder`|  
|![Иерархическое представление не в фокусе при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Без фокуса ввода**|Историческая справка|`TreeView.SelectedItemInactive`|  
|![Иерархическое представление не в фокусе при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Без фокуса ввода**|Передний план (текст)|`TreeView.SelectedItemInactive`|  
|![Иерархическое представление не в фокусе при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Без фокуса ввода**|Передний план (глиф)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Иерархическое представление не в фокусе при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Без фокуса ввода**|Граница|None|  
  
#### <a name="button-controls"></a>Элементы управления "Кнопка"  
 ![Красная линия элемента управления "Кнопка"](../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303-155_ButtonControlRedline")  
  
 Используйте:  
 для кнопок в контейнере документа, которые должны интегрироваться с темами Visual Studio (светлая, темная, синяя или системная высококонтрастная тема).  
  
 Не используйте:  
 для кнопок, которые будут отображаться на пользовательском фоне, не входящем в тему Visual Studio.  
  
 **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Кнопку](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Кнопка|`CommonControls.Button`|  
|![Кнопку](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Граница кнопки|`CommonControls.ButtonBorder`|  
  
 **Отключен**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Неактивна кнопка](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Кнопка|`CommonControls.ButtonDisabled`|  
|![Неактивна кнопка](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Граница кнопки|`CommonControls.ButtonBorderDisabled`|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Кнопка при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Кнопка|`CommonControls.ButtonHover`|  
|![Кнопка при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Граница кнопки|`CommonControls.ButtonBorderHover`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Активная кнопка](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Кнопка|`CommonControls.ButtonPressed`|  
|![Активная кнопка](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Граница кнопки|`CommonControls.ButtonBorderPressed`|  
  
 **Focused**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Кнопка в фокусе](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Кнопка|`CommonControls.ButtonFocused`|  
|![Кнопка в фокусе](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Граница кнопки|`CommonControls.ButtonBorderFocused`|  
  
#### <a name="check-box-controls"></a>Элементы управления "Флажок"  
 ![Красная линия флажка](../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303-161_CheckboxRedline")  
  
 Используйте:  
 для элементов управления типа "Флажок", содержащихся в контейнере документа.  
  
 Не используйте:  
 для пользовательского интерфейса, который не является элементом управления "Флажок".  
  
 **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Флажок](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Историческая справка|`CommonControls.CheckBoxBackground`|  
|![Флажок](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Граница|`CommonControls.CheckBoxBorder`|  
|![Флажок](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|текст|`CommonControls.CheckBoxText`|  
|![Флажок](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Глиф|`CommonControls.CheckBoxGlyph`|  
  
 **Отключен**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Неактивный флажок](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Историческая справка|`CommonControls.CheckBoxBackgroundDisabled`|  
|![Неактивный флажок](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Граница|`CommonControls.CheckBoxBorderDisabled`|  
|![Неактивный флажок](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|текст|`CommonControls.CheckBoxTextDisabled`|  
|![Неактивный флажок](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Глиф|`CommonControls.CheckBoxGlyphDisabled`|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Флажок при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Историческая справка|`CommonControls.CheckBoxBackgroundHover`|  
|![Флажок при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Граница|`CommonControls.CheckBoxBorderHover`|  
|![Флажок при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|текст|`CommonControls.CheckBoxTextHover`|  
|![Флажок при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Глиф|`CommonControls.CheckBoxGlyphHover`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Активный флажок](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Историческая справка|`CommonControls.CheckBoxBackgroundPressed`|  
|![Активный флажок](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Граница|`CommonControls.CheckBoxBorderPressed`|  
|![Активный флажок](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|текст|`CommonControls.CheckBoxTextPressed`|  
|![Активный флажок](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Глиф|`CommonControls.CheckBoxGlyphPressed`|  
  
 **Focused**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Флажок с фокусом ввода](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Историческая справка|`CommonControls.CheckBoxBackgroundFocused`|  
|![Флажок с фокусом ввода](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Граница|`CommonControls.CheckBoxBorderFocused`|  
|![Флажок с фокусом ввода](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|текст|`CommonControls.CheckBoxTextFocused`|  
|![Флажок с фокусом ввода](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Глиф|`CommonControls.CheckBoxGlyphFocused`|  
  
#### <a name="drop-boxcombo-box-controls"></a>Элементы управления "Раскрывающийся список" и "Поле со списком"  
 ![Падение&#45;вниз&#47;комбо окно красной линии](../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")  
  
Используйте:  
для раскрывающихся списков и полей со списком, которые являются частью контейнера документа.  

Не используйте:  
- для других элементов пользовательского интерфейса, не являющихся раскрывающимися списками или полями со списком;  

- для [Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown) или [Combo box](../misc/shared-colors.md#BKMK_CommandComboBox) на панели команд.  
  
  **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Падение&#45;вниз&#47;комбо-коробку](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Историческая справка|`CommonControls.ComboBoxBackground`|  
|![Падение&#45;вниз&#47;комбо-коробку](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Граница|`CommonControls.ComboBoxBorder`|  
|![Падение&#45;вниз&#47;комбо-коробку](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|текст|`CommonControls.ComboBoxText`|  
|![Падение&#45;вниз&#47;комбо-коробку](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Разделитель|`CommonControls.ComboBoxSeparator`|  
|![Падение&#45;вниз&#47;комбо-коробку](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Глиф|`CommonControls.ComboBoxGlyph`|  
|![Падение&#45;вниз&#47;комбо-коробку](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Фон глифа|`CommonControls.ComboBoxGlyphBackground`|  
  
 **Отключен**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Падение&#45;вниз&#47;комбо-коробка отключена](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Историческая справка|`CommonControls.ComboBoxBackgroundDisabled`|  
|![Падение&#45;вниз&#47;комбо-коробка отключена](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Граница|`CommonControls.ComboBoxBorderDisabled`|  
|![Падение&#45;вниз&#47;комбо-коробка отключена](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|текст|`CommonControls.ComboBoxTextDisabled`|  
|![Падение&#45;вниз&#47;комбо-коробка отключена](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Разделитель|`CommonControls.ComboBoxSeparatorDisabled`|  
|![Падение&#45;вниз&#47;комбо-коробка отключена](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Глиф|`CommonControls.ComboBoxGlyphDisabled`|  
|![Падение&#45;вниз&#47;комбо-коробка отключена](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Фон глифа|`CommonControls.ComboBoxGlyphBackgroundDisabled`|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Падение&#45;вниз&#47;комбо поле на нависть](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Историческая справка|`CommonControls.ComboBoxBackgroundHover`|  
|![Падение&#45;вниз&#47;комбо поле на нависть](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Граница|`CommonControls.ComboBoxBorderHover`|  
|![Падение&#45;вниз&#47;комбо поле на нависть](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|текст|`CommonControls.ComboBoxTextHover`|  
|![Падение&#45;вниз&#47;комбо поле на нависть](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Разделитель|`CommonControls.ComboBoxSeparatorHover`|  
|![Падение&#45;вниз&#47;комбо поле на нависть](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Глиф|`CommonControls.ComboBoxGlyphHover`|  
|![Падение&#45;вниз&#47;комбо поле на нависть](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Фон глифа|`CommonControls.ComboBoxGlyphBackgroundHover`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Падение&#45;вниз&#47;комбо-коробка нажата](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Историческая справка|`CommonControls.ComboBoxBackgroundPressed`|  
|![Падение&#45;вниз&#47;комбо-коробка нажата](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Граница|`CommonControls.ComboBoxBorderPressed`|  
|![Падение&#45;вниз&#47;комбо-коробка нажата](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|текст|`CommonControls.ComboBoxTextPressed`|  
|![Падение&#45;вниз&#47;комбо-коробка нажата](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Разделитель|`CommonControls.ComboBoxSeparatorPressed`|  
|![Падение&#45;вниз&#47;комбо-коробка нажата](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Глиф|`CommonControls.ComboBoxGlyphPressed`|  
|![Падение&#45;вниз&#47;комбо-коробка нажата](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Фон глифа|`CommonControls.ComboBoxGlyphBackgroundPressed`|  
  
 **Focused**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Падение&#45;вниз&#47;комбо-коробка сосредоточена](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Историческая справка|`CommonControls.ComboBoxBackgroundFocused`|  
|![Падение&#45;вниз&#47;комбо-коробка сосредоточена](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Граница|`CommonControls.ComboBoxBorderFocused`|  
|![Падение&#45;вниз&#47;комбо-коробка сосредоточена](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|текст|`CommonControls.ComboBoxTextFocused`|  
|![Падение&#45;вниз&#47;комбо-коробка сосредоточена](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Разделитель|`CommonControls.ComboBoxSeparatorFocused`|  
|![Падение&#45;вниз&#47;комбо-коробка сосредоточена](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Глиф|`CommonControls.ComboBoxGlyphFocused`|  
|![Падение&#45;вниз&#47;комбо-коробка сосредоточена](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Фон глифа|`CommonControls.ComboBoxGlyphBackgroundFocused`|  
  
 **Выделение текста в поле ввода**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Падение&#45;вниз&#47;комбо-коробка текст ввода](../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")|Выделение|`CommonControls.ComboBoxTextInputSelection`|  
  
 **Активный — представление элемента списка**  
  
|Компонент|Элемент|Имя токена: Цвет.категория|  
|---------------|-------------|--------------------------------|  
|![Падение&#45;вниз&#47;комбо поле список представления](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Историческая справка|`CommonControls.ComboBoxListBackground`|  
|![Падение&#45;вниз&#47;комбо поле список представления](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Историческая справка|`CommonControls.ComboBoxListBackgroundHover`|  
|![Падение&#45;вниз&#47;комбо поле список представления](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Историческая справка|`CommonControls.ComboBoxListItemBackgroundPressed`|  
|![Падение&#45;вниз&#47;комбо поле список представления](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Историческая справка|`CommonControls.ComboBoxListItemBackgroundFocused`|  
|![Падение&#45;вниз&#47;комбо поле список представления](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Граница|`CommonControls.ComboBoxListBorder`|  
|![Падение&#45;вниз&#47;комбо поле список представления](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Граница|`CommonControls.ComboBoxListBorderHover`|  
|![Падение&#45;вниз&#47;комбо поле список представления](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Граница|`CommonControls.ComboBoxListBorderPressed`|  
|![Падение&#45;вниз&#47;комбо поле список представления](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Граница|`CommonControls.ComboBoxListBorderFocused`|  
|![Падение&#45;вниз&#47;комбо поле список представления](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Текст элемента|`CommonControls.ComboBoxListItemText`|  
|![Падение&#45;вниз&#47;комбо поле список представления](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Текст элемента|`CommonControls.ComboBoxListItemTextHover`|  
|![Падение&#45;вниз&#47;комбо поле список представления](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Текст элемента|`CommonControls.ComboBoxListItemTextPressed`|  
|![Падение&#45;вниз&#47;комбо поле список представления](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Текст элемента|`CommonControls.ComboBoxListItemTextFocused`|  
|![Падение&#45;вниз&#47;комбо поле список представления](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Фон с тенью|`CommonControls.ComboBoxListBackgroundShadow`|  
  
#### <a name="tabular-data-grid-controls"></a>Табличные элементы управления данными (сетка)  
 Табличные элементы управления данными, также называемые элементами управления "Сетка", — это стандартные элементы управления Visual Studio, которые можно использовать для представления больших объемов данных в нескольких столбцах. Стандартные табличные элементы управления данными встречаются в Visual Studio в нескольких местах: в окне инструментов "Список ошибок", в отчетах IntelliTrace, в представлении кучи памяти и т. д. Всегда используйте стандартные табличные элементы управления данными. Однако в некоторых редких случаях доступ к стандартным табличным элементам управления данными может отсутствовать. В таких ситуациях используйте указанные ниже имена токенов для обеспечения согласованности пользовательского интерфейса с другими табличными элементами управления данными в Visual Studio.  
  
 ![Табулярные данные &#40;контроль сетки&#41; красную линию](../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")  
  
 Используйте:  
 для табличных элементов управления или элементов управления "Сетка".  
  
 Не используйте:  
 для элементов пользовательского интерфейса, которые не являются табличными элементами управления или элементами управления "Сетка".  
  
##### <a name="column-headers"></a>Заголовки столбцов  
 Заголовки столбцов состоят из фона, границы, текста заголовка и необязательного глифа, который обычно используется при сортировке сетки по данному столбцу.  
  
|Штат|Элемент|Имя токена: Category.color|  
|-----------|-------------|--------------------------------|  
|По умолчанию|Историческая справка|`Header.Default`|  
|По умолчанию|Передний план (текст)|`Environment.CommandBarTextActive`|  
|По умолчанию|Передний план (глиф)|`Header.Glyph`|  
|По умолчанию|Граница|`Header.SeparatorLine`|  
|Наведение|Историческая справка|`Header.MouseOver`|  
|Наведение|Передний план (текст)|`Environment.CommandBarTextHover`|  
|Наведение|Передний план (глиф)|`Header.MouseOverGlyph`|  
|Наведение|Граница|`Header.SeparatorLine`|  
|Нажато|Историческая справка|`CommonControls.CheckBoxBackgroundPressed`|  
|Нажато|Передний план (текст)|`CommonControls.CheckBoxBorderPressed`|  
|Нажато|Передний план (глиф)|`CommonControls.CheckBoxTextPressed`|  
|Нажато|Граница|`CommonControls.CheckBoxGlyphPressed`|  
  
##### <a name="list-view-items"></a>Элементы представления списка  
 Элементы представления списка состоят из фона и содержимого. Содержимым может быть текст, значок или и то и другое.  
  
|Штат|Элемент|Имя токена: Category.color|  
|-----------|-------------|--------------------------------|  
|По умолчанию|Историческая справка|Прозрачный|  
|По умолчанию|Передний план (текст)|`Environment.CommandBarTextActive`|  
|По умолчанию|Граница|None|  
|Выбран (активен)|Историческая справка|`TreeView.SelectedItemActive`|  
|Выбран (активен)|Передний план (текст)|`TreeView.SelectedItemActiveText`|  
|Выбран (активен)|Граница|None|  
|Выбран (неактивен)|Историческая справка|`TreeView.SelectedItemInactive`|  
|Выбран (неактивен)|Передний план (текст)|`TreeView.SelectedItemInactiveText`|  
|Выбран (неактивен)|Граница|None|  
  
### <a name="manifest-designer"></a>Конструктор манифеста  
 Конструктор манифеста призван упростить редактирование файла манифеста в проектах Windows 8 и Windows Phone 8. Хотя общего готового шаблона нет, рекомендуется обеспечивать соответствие макету и цветам вкладок ориентации и навигации, а также общей структуре. Дополнительные сведения о макете см. в разделе [Layout for Visual Studio](../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![Красная линия конструктора манифеста](../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303-175_ManifestDesignerRedline")  
  
Используйте:  
- для конструкторов, которые похожи на конструктор манифеста;  

- вместо использования стандартных элементов управления типа "Вкладка" в верхней части редактора в контейнере документа.  

Не используйте:  
- при наличии более чем шести вкладок;  

- для пользовательского интерфейса, который отличается структурой от конструктора манифеста.  
  
|Штат|Компонент|Элемент|Имя токена: Category.color|  
|-----------|---------------|-------------|--------------------------------|  
|По умолчанию (выбрано)|Вкладка|Историческая справка|`ManifestDesigner.TabActive`|  
|По умолчанию (выбрано)|Вкладка|Граница|None|  
|По умолчанию (выбрано)|Панель описания|Историческая справка|`ManifestDesigner.DescriptionPane`|  
|По умолчанию (выбрано)|Страница содержимого|Историческая справка|`ManifestDesigner.Background`|  
|По умолчанию (выбрано)|Страница содержимого|Текст подсказки для диалогового окна|`ManifestDesigner.WatermarkText`<br /><br /> Это имя токена не соответствует его функции.|  
|Не выбрано|Вкладка|Историческая справка|`ManifestDesigner.Tab.Inactive`|  
|Наведение|Вкладка|Историческая справка|`ManifestDesigner.Tab.Mouseover`|  
  
### <a name="tagging"></a>Добавление тегов  
 Visual Studio поддерживает добавление тегов, что позволяет пользователю объявлять доступные для поиска ключевые слова в целях отслеживания. Например, руководители проектов и разработчики могут использовать Team Foundation Server (TFS) для добавления тегов к рабочим элементам. В приведенных ниже таблицах представлены имена цветов как для самого тега, так и для глифа (значка закрытия), который появляется при наведении указателя и в некоторых состояниях.  
  
 ![Красная линия пометки тегами](../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303-176_TaggingRedline")  
  
 Используйте:  
 для пользовательского интерфейса, который поддерживает добавление тегов.  
  
 Не используйте:  
 для любого другого пользовательского интерфейса.  
  
#### <a name="tag"></a>Тег  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Тег](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **По умолчанию**|Историческая справка|`Tag.Background`|  
|![Тег](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **По умолчанию**|Передний план (текст)|`Tag.Background`|  
|![Тег при наведении указателя мыши](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Наведение**|Историческая справка|`Tag.HoverBackground`|  
|![Тег при наведении указателя мыши](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Наведение**|Передний план (текст)|`Tag.HoverBackgroundText`|  
|![Активный тег](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Нажато**|Историческая справка|`Tag.PressedBackground`|  
|![Активный тег](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Нажато**|Передний план (текст)|`Tag.PressedBackgroundText`|  
|![Выбранный тег](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Выбрано**|Историческая справка|`Tag.SelectedBackground`|  
|![Выбранный тег](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Выбрано**|Передний план (текст)|`Tag.SelectedBackgroundText`|  
  
#### <a name="glyph-close-icon"></a>Глиф (значок закрытия)  
 **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Тег &#40;глиф&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **По умолчанию (тег по умолчанию)**|Историческая справка|Недоступно|  
|![Тег &#40;глиф&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **По умолчанию (тег по умолчанию)**|Передний план (глиф)|`Tag.TagHoverGlyph`|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Тег &#40;глиф&#41; на нависть](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **При наведении указателя (тег по умолчанию)**|Историческая справка|`Tag.TagHoverGlyphHoverBackground`|  
|![Тег &#40;глиф&#41; на нависть](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **При наведении указателя (тег по умолчанию)**|Передний план (глиф)|`Tag.TagHoverGlyphHover`|  
|![Тег &#40;глиф&#41; на нависть](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **При наведении указателя (тег по умолчанию)**|Граница|`Tag.TagHoverGlyphHoverBorder`|  
  
 **Нажато**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Тег &#40;глиф&#41; нажата](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Активен (тег по умолчанию)**|Историческая справка|`Tag.TagHoverGlyphPressedBackground`|  
|![Тег &#40;глиф&#41; нажата](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Активен (тег по умолчанию)**|Передний план (глиф)|`Tag.TagHoverGlyphPressed`|  
|![Тег &#40;глиф&#41; нажата](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Активен (тег по умолчанию)**|Граница|`Tag.TagHoverGlyphPressedBorder`|  
  
 **Тег выбран/глиф по умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Выбранный тег](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **По умолчанию (активный тег)**|Историческая справка|Недоступно|  
|![Выбранный тег](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **По умолчанию (активный тег)**|Передний план (глиф)|`Tag.TagSelectedGlyph`|  
  
 **Тег выбран/глиф при наведении указателя**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Выбранный тег при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **При наведении указателя (тег выбран)**|Историческая справка|`Tag.TagSelectedGlyphHoverBackground`|  
|![Выбранный тег при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **При наведении указателя (тег выбран)**|Передний план (глиф)|`Tag.TagSelectedGlyphHover`|  
|![Выбранный тег при наведении курсора мыши](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **При наведении указателя (тег выбран)**|Граница|`Tag.TagSelectedGlyphHoverBorder`|  
  
 **Тег выбран/активный глиф**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Выбранный активный тег](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Активен (тег выбран)**|Историческая справка|`Tag.TagSelectedGlyphPressedBackground`|  
|![Выбранный активный тег](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Активен (тег выбран)**|Передний план (глиф)|`Tag.TagSelectedGlyphPressed`|  
|![Выбранный активный тег](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Активен (тег выбран)**|Граница|`Tag.TagSelectedGlyphPressedBorder`|  
  
### <a name="shell"></a>Оболочка  
  
#### <a name="background"></a>Историческая справка  
 Фон среды состоит из двух слоев. Нижний слой представляет собой сплошной цвет, который охватывает всю интегрированную среду разработки. Верхний слой используется под командной полкой и между каналами автоматического скрытия окон инструментов по левому и правому краям интегрированной среды разработки. Начиная с версии Visual Studio 2013 верхний и нижний слои фона имеют одинаковый цвет при использовании светлой и темной тем.  
  
 ![Красная линия фоновой оболочки](../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303-187_ShellBackgroundRedline")  
  
 Используйте:  
 для областей, которые должны соответствовать фону среды Visual Studio.  
  
Не используйте:  
- в качестве заливки для областей, которые не являются фоновыми;  

- в качестве фона, на котором должны размещаться элементы переднего плана.  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|Нижний слой|Историческая справка|`Environment.EnvironmentBackground`|  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|Верхний слой|Историческая справка<br /><br /> *Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.*|`Environment.EnvironmentBackgroundGradientBegin`|  
|Верхний слой|Историческая справка<br /><br /> *Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.*|`Environment.EnvironmentBackgroundGradientEnd`|  
|Верхний слой|Историческая справка<br /><br /> *Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.*|`Environment.EnvironmentBackgroundGradientMiddle1`|  
|Верхний слой|Историческая справка<br /><br /> *Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.*|`Environment.EnvironmentBackgroundGradientMiddle2`|  
  
#### <a name="command-shelf"></a>Командная полка  
 Для фона командной полки используются два набора имен токенов: один для области размещения строки меню, а другой — для области размещения панелей команд. Отдельные группы на панели команд имеют собственные значения цветов фона, которые более подробно рассматриваются в разделе, посвященном панели команд. Цвета текста строки меню и панели команд рассматриваются в разделах, посвященных меню и панели команд.  
  
 ![Красная линия командной полки](../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303-188_CommandShelfRedline")  
  
Используйте:  
- для областей, где размещаются меню или панели инструментов;  

- с правильным фоном / комбинацией имен маркеров на переднем плане.  
  
  Не используйте:  
  для областей, которые не похожи на командную полку.  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|Строка меню|Историческая справка<br /><br /> *Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.*|`Environment.CommandShelfHighlightGradientBegin`|  
|Строка меню|Историческая справка<br /><br /> *Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.*|`Environment.CommandShelfHighlightGradientMiddle`|  
|Строка меню|Историческая справка<br /><br /> *Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.*|`Environment.CommandShelfHighlightGradientEnd`|  
|Панель команд|Историческая справка<br /><br /> *Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.*|`Environment.CommandShelfBackgroundGradientBegin`|  
|Панель команд|Историческая справка<br /><br /> *Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.*|`Environment.CommandShelfBackgroundGradientMiddle`|  
|Панель команд|Историческая справка<br /><br /> *Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.*|`Environment.CommandShelfBackgroundGradientEnd`|  
  
### <a name="toolbox"></a>Область элементов  
 Панель элементов — одно из стандартных окон инструментов, которое чаще всего используется в Visual Studio. По сути, это элемент управления типа "Дерево" с примененной к нему специальной темой и стилем.  
  
 ![Красная линия панели инструментов](../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303-189_ToolboxRedline")  
  
 Используйте:  
 при разработке окна инструментов, которое всегда должно быть согласовано с панелью элементов оболочки.  
  
 Не используйте:  
 для компонентов, которые не похожи на панель элементов, или если вы опасаетесь, что могут возникнуть проблемы с вашим пользовательским интерфейсом при изменении цветов панели элементов оболочки.  
  
 **По умолчанию**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Родительский узел панели инструментов](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Родительский узел**|Историческая справка|`Environment.ToolboxContent`<br /><br /> Заголовки<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Отдельные элементы или все окно, если нет доступных элементов управления|  
|![Дочерний узел панели инструментов](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Дочерний узел**|Историческая справка|`Environment.ToolboxContent`<br /><br /> Заголовки<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Отдельные элементы или все окно, если нет доступных элементов управления|  
|![Родительский узел панели инструментов](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Родительский узел**|Граница|None|  
|![Дочерний узел панели инструментов](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Дочерний узел**|Граница|None|  
|![Родительский узел панели инструментов](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Родительский узел**|Передний план (глиф)|`Environment.ToolboxContent`|  
|![Дочерний узел панели инструментов](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Дочерний узел**|Передний план (глиф)|`Environment.ToolboxContent`|  
|![Родительский узел панели инструментов](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Родительский узел**|Передний план (текст)|`Environment.ToolboxContent`|  
|![Дочерний узел панели инструментов](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Дочерний узел**|Передний план (текст)|`Environment.ToolboxContent`|  
  
 **Наведение**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Дочерний узел панели инструментов при наведении указателя мыши](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Наведение указателя на дочерний узел панели элементов**|Историческая справка|`Environment.ToolboxContentMouseOver`<br /><br /> Только отдельные элементы|  
|![Дочерний узел панели инструментов при наведении указателя мыши](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Наведение указателя на дочерний узел панели элементов**|Граница|None|  
|![Дочерний узел панели инструментов при наведении указателя мыши](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Наведение указателя на дочерний узел панели элементов**|Передний план (текст)|`Environment.ToolboxContentMouseOver`<br /><br /> Только отдельные элементы|  
  
 **Выбрано**  
  
|Компонент|Элемент|Имя токена: Category.color|  
|---------------|-------------|--------------------------------|  
|![Родительский узел панели инструментов в фокусе](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Родительский узел с фокусом ввода**|Историческая справка|`TreeView.SelectedItemActive`<br /><br /> Из категории [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Дочерний узел панели инструментов в фокусе](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Дочерний узел с фокусом ввода**|Историческая справка|`TreeView.SelectedItemActive`<br /><br /> Из категории [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Родительский узел панели инструментов в фокусе](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Родительский узел с фокусом ввода**|Граница|`TreeView.FocusVisualBorder`<br /><br /> Из категории [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Дочерний узел панели инструментов в фокусе](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Дочерний узел с фокусом ввода**|Граница|`TreeView.FocusVisualBorder`<br /><br /> Из категории [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Родительский узел панели инструментов в фокусе](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Родительский узел с фокусом ввода**|Передний план (глиф)|`TreeView.SelectedItemActive`<br /><br /> Из категории [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Дочерний узел панели инструментов в фокусе](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Дочерний узел с фокусом ввода**|Передний план (глиф)|`TreeView.SelectedItemActive`<br /><br /> Из категории [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Родительский узел панели инструментов в фокусе](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Родительский узел с фокусом ввода**|Передний план (текст)|`TreeView.SelectedItemActive`<br /><br /> Из категории [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Дочерний узел панели инструментов в фокусе](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Дочерний узел с фокусом ввода**|Передний план (текст)|`TreeView.SelectedItemActive`<br /><br /> Из категории [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Родительский узел панели инструментов без фокуса ввода](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Родительский узел без фокуса ввода**|Историческая справка|`TreeView.SelectedItemInactive`<br /><br /> Из категории [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Дочерний узел панели инструментов без фокуса ввода](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Дочерний узел без фокуса ввода**|Историческая справка|`TreeView.SelectedItemInactive`<br /><br /> Из категории [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Родительский узел панели инструментов без фокуса ввода](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Родительский узел без фокуса ввода**|Граница|None|  
|![Дочерний узел панели инструментов без фокуса ввода](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Дочерний узел без фокуса ввода**|Граница|None|  
|![Родительский узел панели инструментов без фокуса ввода](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Родительский узел без фокуса ввода**|Передний план (глиф)|`TreeView.SelectedItemInactive`<br /><br /> Из категории [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Дочерний узел панели инструментов без фокуса ввода](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Дочерний узел без фокуса ввода**|Передний план (глиф)|`TreeView.SelectedItemInactive`<br /><br /> Из категории [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Родительский узел панели инструментов без фокуса ввода](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Родительский узел без фокуса ввода**|Передний план (текст)|`TreeView.SelectedItemInactive`<br /><br /> Из категории [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Дочерний узел панели инструментов без фокуса ввода](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Дочерний узел без фокуса ввода**|Передний план (текст)|`TreeView.SelectedItemInactive`<br /><br /> Из категории [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
  
## <a name="color-value-reference"></a>Справочник по значениям цвета  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|Компонент|Часть|Элемент|Штат|Светлый|Dark|Синий|Высокая контрастность|  
|Разделительные строки|||По умолчанию|FFEEEEF2|FF2D2D30|FFEEEEF2|ControlDark|  
|Глиф развертывания||Передний план|По умолчанию|||||  
|Глиф развертывания||Передний план|Наведение|||||  
|Глиф развертывания||Историческая справка|По умолчанию|||||  
|Глиф развертывания||Историческая справка|Наведение|||||  
|Глиф развертывания||Граница|По умолчанию|||||  
|Глиф развертывания||Граница|Наведение|||||