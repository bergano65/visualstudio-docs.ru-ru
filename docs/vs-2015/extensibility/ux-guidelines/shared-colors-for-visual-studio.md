---
title: Общие цвета
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 87520a7e17d194d7f5cc28665a6f23466bface65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154596"
---
# <a name="shared-colors-for-visual-studio"></a>Общие цвета для Visual Studio

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Если вы разрабатываете пользовательский интерфейс, в котором используются стандартные элементы оболочки Visual Studio, или вам нужно обеспечить согласованность элемента интерфейса с аналогичными функциями, используйте существующие имена токенов в файлах определения пакетов для выбора и назначения цветов. Таким образом можно обеспечить согласованность пользовательского интерфейса со всей средой Visual Studio и его автоматическое обновление при добавлении или обновлении тем.

В этом разделе описываются стандартные элементы пользовательского интерфейса и используемые ими имена токенов, на которые можно ссылаться при разработке похожего пользовательского интерфейса. Более подробные сведения о доступе к этим токенам цветов см. в разделе [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Используйте имена токенов правильно.

- **Используйте имена токенов в соответствии с функцией, а не самим цветом.** Стандартные общие цвета связаны с определенными элементами интерфейса и предназначены для использования только для аналогичных или похожих функций. Например, не используйте цвет выбранного поля со списком для анимированного индикатора хода выполнения только потому, что вам понравился цвет. Функции поля со списком и анимированного индикатора различны, и если цвет, связанный с полем со списком, изменится, он может оказаться неподходящим для анимированного элемента. Согласованное использование цветов помогает пользователям ориентироваться в интерфейсе и предотвращает путаницу.

- **Используйте цвета фона и текста в правильном сочетании.** Цвет фона, предназначенный для текста, имеет соответствующий цвет текста. Не используйте цвета текста, отличные от тех, которые определены для данного цвета фона. Если с цветом фона не связан цвет текста, не используйте его для поверхности, на которой будет выводиться текст. Другие сочетания цветов текста и фона могут сделать интерфейс неудобным для восприятия.

- **Используйте цвета элементов управления, соответствующие их расположению.** В определенных состояниях некоторые элементы управления Visual Studio не имеют отдельных цветов границ и фона. Эти цвета наследуются от областей, в которых они расположены. Всегда используйте имена токенов, которые подходят для того места, в котором вы размещаете элементы управления.

> [!IMPORTANT]
> Не используйте токены, найденные в категориях "Начальная страница" или "Cider".

## <a name="command-structures"></a>Структура команд

### <a name="menus"></a><a name="BKMK_CommandMenus"></a> Ярлык

Меню могут находиться в нескольких местах в Visual Studio: в главной строке меню, внедренной в документ или в окнах инструментов, или при щелчке правой кнопкой мыши в различных местах в интегрированной среде разработки. Реализация меню, связанных с другими элементами пользовательского интерфейса, рассматривается в разделах, посвященных соответствующим элементам. Всегда используйте стандартную реализацию меню, предоставляемую средой Visual Studio. Однако в некоторых редких случаях доступ к стандартным меню Visual Studio может отсутствовать. В таких ситуациях используйте указанные ниже имена токенов для обеспечения согласованности пользовательского интерфейса с другими меню в Visual Studio.

![Красная линия меню](../../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303 — 000_MenuRedline")

Используйте:
- если нужно создать пользовательское меню;

- если есть новый компонент пользовательского интерфейса, который должен соответствовать меню Visual Studio.

Не используйте:
цвет фона сам по себе. Всегда используйте определенное сочетание цвета фона и цвета переднего плана.

#### <a name="menu-title"></a>Заголовок меню

Заголовок меню состоит из фона, границы и текста заголовка, а также необязательного глифа (обычно если меню находится на панели команд).

![Красная линия заголовка меню](../../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303 — 001_MenuTitleRedline")

Используйте:
при создании пользовательского заголовка меню.

Не используйте:
- для каких-либо элементов, которые не должны всегда соответствовать заголовку меню;

- в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.

  **Default**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Заголовок меню по умолчанию](../../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 — 002_MenuTitleDefault")

  **Заголовок меню**

  Фон

  None

  Передний план (текст)

  `Environment.CommandBarTextActive`

  ![Заголовок меню с глифом по умолчанию](../../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 — 003_MenuTitleWithGlyphDefault")

  **Заголовок меню с глифом**

  Передний план (глиф)

  `Environment.CommandBarMenuGlyph`

  Рамка

  None

  **Наведение**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Заголовок меню при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 — 004_MenuTitleHover")

  **Заголовок меню**

  Фон

  `Environment.CommandBarMouseOverBackgroundBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст)

  `Environment.CommandBarTextHover`

  ![Заголовок меню с глифом при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 — 005_MenuTitleWithGlyphHover")

  **Заголовок меню с глифом**

  Передний план (глиф)

  `Environment.CommandBarMenuMouseOverGlyph`

  Рамка

  `Environment.CommandBarBorder`

  **Pressed**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Активная кнопка заголовка меню](../../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 — 006_MenuTitlePressed")

  **Заголовок меню**

  Фон

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст)

  `Environment.CommandBarTextActive`

  ![Активная кнопка заголовка меню с глифом](../../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 — 007_MenuTitleWithGlyphPressed")

  **Заголовок меню с глифом**

  Передний план (глиф)

  `Environment.CommandBarMenuMouseDownGlyph`

  Рамка

  `Environment.CommandBarMenuBorder`

  Только с левой, верхней и правой сторон.

  **Отключен**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Неактивная кнопка заголовка меню с глифом](../../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 — 008_MenuTitleWithGlyphDisabled")

  **Заголовок меню с глифом**

  Фон

  None

  Передний план (текст)

  `Environment.CommandBarTextInactive`

  Передний план (глиф)

  `Environment.CommandBarTextInactive`

  Рамка

  None

#### <a name="menu"></a>Меню

Отдельный пункт меню состоит из текста и необязательных значка, флажка или глифа подменю. Его цвета фона и текста меняются при наведении указателя. Этот токен цвета представляет собой пару, состоящую из цвета фона и цвета переднего плана.

![Красная линия пунктов меню](../../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303 — 009_MenuItemRedline")

Используйте:
для любого раскрывающегося списка, открывающегося из строки меню или панели команд.

Не используйте:
- для любого раскрывающегося списка, открывающегося в другом контексте;

- в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.

  **Default**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Меню по умолчанию](../../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 — 010_MenuDefault")

  **Меню**

  Фон

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст)

  `Environment.CommandBarTextActive`

  Передний план (глиф подменю)

  `Environment.CommandBarMenuSubmenuGlyph`

  Рамка

  `Environment.CommandBarMenuBorder`

  Фон канала значка

  `Environment.CommandBarMenuIconBackground`

  Separator

  `Environment.CommandBarMenuSeparator`

  Shadow

  `Environment.DropShadowBackground`

  ![Меню с установленным флажком](../../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 — 011_MenuChecked")

  **Отмечен**

  Флажок

  `Environment.CommandBarCheckBox`

  Фон флажка

  `Environment.CommandBarSelectedIcon`

  ![Выбранное меню](../../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 — 012_MenuSelected")

  **Selected**

  Фон значка

  `Environment.CommandBarSelected`

  Граница значка

  `Environment.CommandBarSelectedBorder`

  **Наведение**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Меню при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 — 013_MenuHover")

  **Пункт меню**

  Фон

  `Environment.CommandBarMenuItemMouseOver`

  Передний план (текст)

  `Environment.CommandBarMenuItemMouseOver`

  Передний план (глиф подменю)

  `Environment.CommandBarMenuMouseOverSubmenuGlyph`

  ![Меню при наведении курсора мыши с установленным флажком ](../../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 — 014_MenuHoverChecked")

  **Отмечен**

  Флажок

  `Environment.CommandBarCheckBoxMouseOver`

  Фон флажка

  `Environment.CommandBarHoverOverSelectedIcon`

  ![Выбранное меню при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 — 015_MenuHoverSelected")

  **Selected**

  Фон значка

  `Environment.CommandBarHoverOverSelected`

  Граница значка

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Отключен**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Неактивное меню](../../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 — 016_MenuDisabled")

  Элемент меню

  Передний план (текст)

  `Environment.CommandBarTextInactive`

  Передний план (глиф подменю)

  `Environment.CommandBarMenuSubmenuGlyph`

  ![Неактивное меню с установленным флажком](../../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 — 017_MenuDisabledChecked")

  Флажок установлен

  Флажок

  `Environment.CommandBarCheckBoxDisabled`

  Фон флажка

  `Environment.CommandBarSelectedIconDisabled`

### <a name="command-bar"></a>Панель команд

Панель команд может встречаться в интегрированной среде разработки Visual Studio в нескольких местах. В первую очередь это командная полка и окна инструментов и документов.

Как правило, следует всегда использовать стандартную реализацию панели команд, предоставляемую средой Visual Studio. Использование стандартного механизма обеспечивает правильное отображение визуальных элементов и согласованное поведение интерактивных элементов и других элементов управления панели команд Visual Studio. Однако если вам необходимо создать собственную панель команд, следует правильно оформить ее с помощью указанных ниже имен токенов.

![Красная линия командной строки](../../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303 — 018_CommandBarRedline")

![Красная линия кнопки переполнения](../../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303 — 019_OverflowButtonRedline")

Используйте:
в местах, где требуется внедренная панель команд, но нельзя использовать стандартную реализацию панели команд Visual Studio.

Не используйте:
- для элементов пользовательского интерфейса, которые не похожи на панель команд;

- для компонентов панели команд, отличных от тех, для которых определены имена токенов.

#### <a name="command-bar-group"></a>Группа панели команд

Группа панели команд состоит из связанного набора элементов управления панели команд и может содержать любое количество кнопок, разворачивающихся кнопок, раскрывающихся меню, полей со списками или меню. Цвета этих элементов управления определяются отдельными именами токенов, которые рассматриваются в других частях этого руководства. Разделительная линия служит для разделения группы на панели команд в связанные подгруппы.

![Групповая красная линия командной строки](../../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303 — 020_CommandBarGroupRedline")

Используйте:
в местах, где требуется внедренная панель команд, но нельзя использовать стандартную реализацию панели команд Visual Studio.

Не используйте:
- для элементов пользовательского интерфейса, которые не похожи на панель команд;

- для компонентов панели команд, отличных от тех, для которых определены имена токенов.

  **По умолчанию** (нет других состояний)

  Элемент

  Имя токена: Category.color

  Фон

  `Environment.CommandBarGradientBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Рамка

  `Environment.CommandBarToolBarBorder`

  Маркер перетаскивания

  `Environment.CommandBarDragHandle`

  Separator

  `Environment.CommandBarToolBarSeparator`

  `Environment.CommandBarToolBarSeparatorHighlight`

#### <a name="command-icons"></a>Значки команд

![Красная линия значка команды](../../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303 — 021_CommandIconRedline1")

![Красная линия значка команды](../../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303 — 022_CommandIconRedline2")

Используйте:
для кнопок, которые будут размещаться на панели команд.

Не используйте:
- для элементов управления, которые имеют собственные имена токенов;

- в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.

  **Default**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Значок команды по умолчанию](../../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 — 023_CommandIconDefault")

  **Default**

  Фон

  Н/Д (наследуется от фона панели команд)

  Передний план (текст)

  `Environment.CommandBarTextActive`

  Рамка

  Н/Д

  ![Выбранный значок команды по умолчанию](../../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 — 024_CommandIconDefaultSelected")

  **Selected**

  Фон

  `Environment.CommandBarSelected`

  Передний план (текст)

  `Environment.CommandBarTextSelected`

  Рамка

  `Environment.CommandBarSelectedBorder`

  **Наведение указателя мыши и получение фокуса с клавиатуры**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Значок команды при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 — 025_CommandIconHover")

  **Стандартный при наведении указателя мыши**

  Фон

  `Environment.CommandBarMouseOverBackgroundBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст)

  `Environment.CommandBarTextHover`

  Рамка

  `Environment.CommandBarBorder`

  ![Выбранный значок команды при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 — 026_CommandIconHoverSelected")

  **Выбор при наведении указателя мыши**

  Фон

  `Environment.CommandBarHoverOverSelected`

  Передний план (текст)

  `Environment.CommandBarTextHoverOverSelected`

  Рамка

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Pressed**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Активный значок команды](../../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 — 027_CommandIconPressed")

  **Активный значок команды**

  Фон

  `Environment.CommandBarMouseDownBackgroundBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст)

  `Environment.CommandBarTextMouseDown`

  Рамка

  `Environment.CommandBarBorder`

  **Отключен**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Неактивный значок команды](../../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 — 028_CommandIconDisabled")

  **Неактивный значок команды**

  Фон

  Н/Д (наследуется от фона панели команд)

  Передний план (текст)

  `Environment.CommandBarTextInactive`

  Рамка

  Н/Д

#### <a name="combo-box"></a><a name="BKMK_CommandComboBox"></a> Поле со списком

> [!IMPORTANT]
> Поле со списком похоже на раскрывающийся список, но включает область для ввода и редактирования текста. Если раскрывающийся список не включает область для ввода и редактирования текста, используйте токены цветов, указанные в разделе [Drop-down](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Красная линия поля со списком](../../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303 — 029_ComboBoxRedline")

Используйте:
- при создании пользовательских полей со списками;

- при создании элемента управления панели команд, похожего на поле со списком.

  Не используйте:
  - для каких-либо элементов, которые не должны всегда соответствовать пользовательскому интерфейсу панели команд;

- если есть доступ к оформленному полю со списком.

  **Default**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Поле ввода поля со списком](../../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 — 030_ComboBoxInputField")

  **Поле ввода**

  Фон

  `Environment.ComboBoxBackground`

  Передний план (текст)

  `Environment.ComboBoxText`

  Рамка

  `Environment.ComboBoxBorder`

  Separator

  Без разделителя

  ![Кнопка раскрывающегося списка&#45;вниз](../../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 — 031_ComboBoxDropdownButton")

  **Кнопка раскрывающегося списка**

  Фон

  Н/Д (наследуется)

  Передний план (глиф)

  `Environment.ComboBoxGlyph`

  ![Поле со списком&#47;&#45;раскрывающегося списка](../../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 — 032_ComboBoxDropdownList")

  **Раскрывающийся список**

  Фон

  `Environment.ComboBoxPopupBackgroundBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст)

  `Environment.ComboBoxItemText`

  Рамка

  `Environment.ComboBoxPopupBorder`

  **Наведение**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Поле ввода поля со списком при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 — 033_ComboBoxInputFieldHover")

  **Поле ввода**

  Фон

  `Environment.ComboBoxMouseOverBackgroundBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст)

  `Environment.ComboBoxMouseOverText`

  Рамка

  `Environment.ComboBoxMouseOverBorder`

  Separator

  `Environment.ComboBoxMouseOverSeparator`

  ![Поле со списком&#47;удалить&#45;кнопку "вниз" при наведении указателя](../../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 — 034_ComboBoxDropdownButtonHover")

  **Кнопка раскрывающегося списка**

  Фон

  `Environment.ComboBoxButtonMouseOverBackground`

  Передний план (глиф)

  `Environment.ComboBoxMouseOverGlyph`

  ![Поле со списком&#47;&#45;раскрывающегося списка при наведении указателя](../../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 — 035_ComboBoxDropdownListHover")

  **Раскрывающийся список**

  Фон (пункт меню)

  `Environment.ComboBoxItemMouseOverBackground`

  Передний план (текст)

  `Environment.ComboBoxItemMouseOverText`

  Граница (пункт меню)

  `Environment.ComboBoxItemMouseOverBorder`

  **Focused**

  Компонент

  Элемент

  Имя токена: Цвет.категория

  ![Поле ввода поля со списком с фокусом ввода](../../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 — 036_ComboBoxInputFieldFocused")

  **Поле ввода**

  Фон

  `Environment.ComboBoxFocusedBackground`

  Передний план (текст)

  `Environment.ComboBoxFocusedText`

  Рамка

  `Environment.ComboBoxFocusedBorder`

  Separator

  `Environment.ComboBoxFocusedButtonSeparator`

  ![Поле со списком&#47;кнопка "удалить&#45;"](../../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 — 037_ComboBoxDropdownButtonFocused")

  **Кнопка раскрывающегося списка**

  Фон

  `Environment.ComboBoxFocusedButtonBackground`

  Передний план (глиф)

  `Environment.ComboBoxFocusedGlyph`

  **Pressed**

  Компонент

  Элемент

  Имя токена: Цвет.категория

  ![Активное поле ввода поля со списком](../../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 — 038_ComboBoxInputFieldPressed")

  **Поле ввода**

  Фон

  `Environment.ComboBoxMouseDownBackground`

  Передний план (текст)

  `Environment.ComboBoxMouseDownText`

  Рамка

  `Environment.ComboBoxMouseDownBorder`

  Separator

  `Environment.ComboBoxMouseDownSeparator`

  ![Поле со списком&#47;нажатой кнопки "удалить&#45;"](../../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 — 039_ComboBoxDropdownButtonPressed")

  **Кнопка раскрывающегося списка**

  Фон

  `Environment.ComboBoxButtonMouseDownBackground`

  Передний план (глиф)

  `Environment.ComboBoxMouseDownGlyph`

  **Отключен**

  ![Неактивное поле ввода поля со списком](../../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 — 041_ComboBoxInputFieldDisabled")

  **Поле ввода**

  Фон

  `Environment.ComboBoxDisabledBackground`

  Передний план (текст)

  `Environment.ComboBoxDisabledText`

  Рамка

  `Environment.ComboBoxDisabledBorder`

  Separator

  Без разделителя

  ![Поле со списком&#47;кнопка "удалить&#45;" отключена](../../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 — 040_ComboBoxDropdownButtonDisabled")

  **Кнопка раскрывающегося списка**

  Фон

  None

  Передний план (глиф)

  `Environment.ComboBoxDisabledGlyph`

#### <a name="drop-down"></a><a name="BKMK_CommandDropDown"></a> Раскрывающийся список

> [!IMPORTANT]
> Раскрывающийся список похож на поле со списком, но не имеет области для ввода и редактирования текста. Если раскрывающийся список включает область для ввода и редактирования текста, используйте токены цветов, указанные в разделе [Combo box](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Удалить&#45;вниз красная линия](../../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303 — 042_DropdownRedline")

Используйте:
при создании пользовательских элементов управления типа "раскрывающийся список".

Не используйте:
- для каких-либо элементов, отличных от раскрывающегося списка;

- для полей со списками или разворачивающихся кнопок.

  **Default**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Удалить&#45;поле выбора](../../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 — 043_DropdownSelectionField")

  **Поле выбора**

  Фон

  `Environment.DropDownBackground`

  Передний план (текст)

  `DropDownText`

  Рамка

  `DropDownBorder`

  Separator

  Без разделителя

  ![Кнопка "удалить&#45;вниз"](../../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 — 044_DropdownButton")

  **Кнопка раскрывающегося списка**

  Фон

  None

  Передний план (глиф)

  `Environment.DropDownGlyph`

  ![Удалить&#45;список](../../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 — 045_DropdownList")

  **Раскрывающийся список**

  Фон

  `Environment.DropDownPopupBackgroundBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст)

  `Environment.ComboBoxItemText`

  Рамка

  `Environment.DropDownPopupBorder`

  Shadow

  `Environment.DropShadowBackground`

  **Наведение**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Удалить&#45;поле выбора при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 — 046_DropdownSelectionFieldHover")

  **Поле выбора**

  Фон

  `Environment.DropDownMouseOverBackgroundBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст)

  `Environment.DropDownMouseOverText`

  Рамка

  `Environment.DropDownMouseOverBorder`

  Separator

  `Environment.DropDownButtonMouseOverSeparator`

  ![Удалить&#45;кнопку "вниз" при наведении указателя](../../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 — 047_DropdownButtonHover")

  **Кнопка раскрывающегося списка**

  Фон

  `Environment.DropDownButtonMouseOverBackground`

  Передний план (глиф)

  `Environment.DropDownMouseOverGlyph`

  ![Удалить&#45;список при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 — 048_DropdownListHover")

  **Раскрывающийся список**

  Фон (пункт меню)

  `Environment.ComboBoxItemMouseOverBackground`

  Передний план (текст)

  `Environment.ComboBoxItemMouseOverText`

  Граница (пункт меню)

  `Environment.ComboBoxItemMouseOverBorder`

  **Pressed**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Перетащите выделенное поле&#45;вниз](../../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 — 049_DropdownSelectionFieldPressed")

  **Поле выбора**

  Фон

  `Environment.DropDownMouseDownBackground`

  Передний план (текст)

  `Environment.DropDownMouseDownText`

  Рамка

  `Environment.DropDownMouseDownBorder`

  Separator

  `Environment.DropDownButtonMouseDownSeparator`

  ![Нажата кнопка "удалить&#45;" вниз](../../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 — 050_DropdownButtonPressed")

  **Кнопка раскрывающегося списка**

  Фон

  `Environment.DropDownButtonMouseDownBackground`

  Передний план (глиф)

  `Environment.DropDownMouseDownGlyph`

  **Отключен**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Удалить&#45;поле выбора отключено](../../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 — 051_DropdownSelectionFieldDisabled")

  Фон

  `Environment.DropDownDisabledBackground`

  Передний план (текст)

  `Environment.DropDownDisabledText`

  Рамка

  `Environment.DropDownDisabledBorder`

  Separator

  Без разделителя

  ![Кнопка удаления&#45;вниз отключена](../../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 — 052_DropdownButtonDisabled")

  Фон

  Н/Д

  Передний план (глиф)

  `Environment.DropDownDisabledGlyph`

#### <a name="split-button"></a>Разворачивающаяся кнопка

Для разворачивающихся кнопок используются многие имена токенов, определенные для других элементов управления панели команд, таких как кнопки, меню и текст панели команд. Все необходимые имена токенов для действий и кнопок раскрывающихся списков приводятся здесь еще раз для удобства. Раскрывающиеся списки разворачивающихся кнопок являются реализацией [Menus](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)панели команд.

![Красная линия разворачивающейся кнопки](../../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303 — 053_SplitButtonRedline")

Используйте:
при создании пользовательской разворачивающейся кнопки.

Не используйте:
- для других видов кнопок;

- в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.

  **Default**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Разворачивающаяся кнопка](../../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 — 054_SplitButton")

  **Разворачивающаяся кнопка (по умолчанию)**

  Фон

  None

  Передний план (текст)

  `Environment.CommandBarTextActive`

  Передний план (глиф)

  `Environment.CommandBarSplitButtonGlyph`

  Рамка

  Н/Д

  Separator

  Н/Д

  **Наведение**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Разворачивающаяся кнопка при наведении указателя](../../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 — 055_SplitButtonHover")

  **Разворачивающаяся кнопка (при наведении указателя мыши)**

  Фон

  `Environment.CommandBarMouseOverBackgroundBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст)

  `Environment.CommandBarTextHover`

  Передний план (глиф)

  `Environment.CommandBarSplitButtonMouseOverGlyph`

  Рамка

  `Environment.CommandBarBorder`

  Separator

  `Environment.CommandBarSplitButtonSeparator`

  **Pressed**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Нажата кнопка разворачивающегося](../../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 — 056_SplitButtonPressed")

  **Разворачивающаяся кнопка (активная)**

  Фон

  `Environment.CommandBarMouseDownBackgroundBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст)

  `Environment.CommandBarTextMouseDown`

  Передний план (глиф)

  `Environment.CommandBarSplitButtonMouseDownGlyph`

  Рамка

  `Environment.CommandBarBorder`

  Separator

  Н/Д

  **Отключен**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Кнопка разделения отключена](../../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 — 057_SplitButtonDisabled")

  **Разворачивающаяся кнопка (неактивная)**

  Фон

  Н/Д

  Передний план (текст)

  `Environment.ComboBoxItemTextInactive`

  Передний план (глиф)

  `Environment.CommandBarTextInactive`

  Рамка

  Н/Д

  Separator

  Н/Д

#### <a name="more-options-and-overflow-buttons"></a>Кнопки "Дополнительно" и "Переполнение"
 Кнопка "Дополнительно" используется, если группа панели команд может настраиваться путем добавления или удаления связанных кнопок. Кнопка "Переполнение" появляется, если панель команд усекается из-за отсутствия места по горизонтали. При ее нажатии открывается меню, содержащее кнопки, которые не поместились на панели команд. Цвета этих двух кнопок определяются одним и тем же набором имен токенов.

 ![Красная линия дополнительных параметров](../../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303 — 058_MoreOptionsRedline")

 Используйте:
для пользовательских кнопок "Дополнительно" и "Переполнение".

 Не используйте:
для кнопок, которые по своему предназначению отличаются от кнопки "Дополнительно" или "Переполнение".

 **Default**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Дополнительные параметры](../../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 — 059_MoreOptions")

 **Дополнительные параметры**

 ![Кнопка переполнения](../../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 — 060_Overflow")

 **Переполнение**

 Фон

 `Environment.CommandBarOptionsBackground`

 Передний план (глиф)

 `Environment.CommandBarOptionsGlyph`

 **Наведение**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Дополнительные параметры при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 — 061_MoreOptionsHover")

 **Дополнительные параметры**

 ![Переполнение при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 — 062_OverflowOptions")

 **Переполнение**

 Фон

 `Environment.CommandBarOptionsMouseOverBackgroundBegin`

 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

 Передний план (глиф)

 `Environment.CommandBarOptionsMouseDownGlyph`

 **Pressed**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Активные дополнительные параметры](../../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 — 063_MoreOptionsPressed")

 **Дополнительные параметры**

 ![Активное переполнение](../../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 — 064_OverflowPressed")

 **Переполнение**

 Фон

 `Environment.CommandBarOptionsMouseDownBackgroundBegin`

 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

 Передний план (глиф)

 `Environment.CommandBarOptionsMouseDownGlyph`

## <a name="document-windows"></a>Окна документов
 Воссоздавать окна документов не нужно, так как они предоставляются средой Visual Studio. Однако может потребоваться использовать цвета, применяемые в окнах документов, чтобы ваш пользовательский интерфейс был согласован с этой частью среды Visual Studio.

 При использовании токенов цветов окна документов будьте внимательны: используйте их только для аналогичных элементов и всегда в парах. В противном случае результат может быть непредвиденным.

### <a name="document-window-frame"></a>Рамка окна документа
 Окна документов могут быть закрепленными в интегрированной среде разработки или перемещаемыми как отдельные окна. Если окно документа является перемещаемым за пределами интегрированной среды разработки, оно по прежнему размещается в контейнере документа и имеет цвета фона, границы, текста и вкладок, которые совпадают с аналогичными цветами в интегрированной среде разработки. Однако документ размещается внутри рамки, которая имеет собственные цвета фона, границы и текста. Если в контейнере документа закреплены окна инструментов, они наследуют поведение и цвет вкладок от имен токенов окна документа.

 ![Красная линия окна закрепленного документа](../../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303 — 065_DockedDocumentWindowRedline")

 **Закрепленное окно документа**

 ![Красная линия окна плавающего документа](../../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303 — 066_FloatingDocumentWindowRedline")

 **Перемещаемое окно документа**

 Используйте:
при создании пользовательского интерфейса, соответствующего окну документа.

 Не используйте:
для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.

 **Default**

 Компонент

 Элемент

 Имя токена: Category.color

 Документ: закрепленный или перемещаемый

 Фон

 Зависит от типа документа

 Передний план (текст)

 Зависит от типа документа

 Рамка

 `Environment.ToolWindowBorder`

 ![Кадр с фокусом ввода](../../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 — 067_FrameFocused")

 **Рамка: перемещаемая, с фокусом ввода**

 Фон

 `Environment.ToolWindowFloatingFrame`

 Передний план (текст)

 `Environment.ToolWindowFloatingFrame`

 Передний план (глиф)

 `Environment.RaftedWindowButtonActiveGlyph`

 Рамка

 `Environment.MainWindowActiveDefaultBorder`

 Граница (глиф)

 `Environment.RaftedWindowButtonActiveBorder`

 Задается как прозрачная

 ![Кадр без фокуса ввода](../../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 — 068_FrameUnfocused")

 **Рамка: перемещаемая, без фокуса ввода**

 Фон

 `Environment.ToolWindowFloatingFrameInactive`

 Передний план (текст)

 `Environment.ToolWindowFloatingFrameInactive`

 Передний план (глиф)

 `Environment.RaftedWindowButtonInactiveGlyph`

 Рамка

 `Environment.MainWindowInactiveBorder`

 Граница (глиф)

 `Environment.RaftedWindowButtonInactiveBorder`

 Задается как прозрачная

 **Наведение**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Кадр с фокусом ввода при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 — 069_FrameFocusedHover")

 **Рамка: перемещаемая, с фокусом ввода**

 Фон (глиф)

 `Environment.RaftedWindowButtonHoverActive`

 Передний план (глиф)

 `Environment.RaftedWindowButtonHoverActiveGlyph`

 Граница (глиф)

 `Environment.RaftedWindowButtonHoverActiveBorder`

 ![Кадр без фокуса ввода при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 — 070_FrameUnfocusedHover")

 **Рамка: перемещаемая, без фокуса ввода**

 Фон (глиф)

 `EnvironmentRaftedWindowButtonHoverInactive`

 Передний план (глиф)

 `Environment.RaftedWindowButtonHoverInactiveGlyph`

 Граница (глиф)

 `Environment.RaftedWindowButtonHoverInactiveBorder`

 **Pressed**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Активный кадр с фокусом ввода](../../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 — 071_FrameFocusedPressed")

 **Рамка: перемещаемая, с фокусом ввода**

 Фон (глиф)

 `Environment.RaftedWindowButtonDown`

 Передний план (глиф)

 `Environment.RaftedWindowButtonDownGlyph`

 Граница (глиф)

 `Environment.RaftedWindowButtonDownBorder`

### <a name="document-tabs"></a>Вкладки документов
 Вкладки документов размещаются в канале вкладок и указывают, какие документы в настоящее время открыты, а также какой документ в настоящий момент выбран или активен. Окна инструментов также могут закрепляться в канале вкладок документов, если пользователь размещает их там. В этом случае для них используются те же цвета, что и для окон документов. Если вы создаете пользовательский интерфейс, цвета которого должны всегда соответствовать цветам окна документа (в том числе при обновлении темы или установке новых тем), то используйте ссылки на указанные ниже токены цветов.

 ![Красная линия вкладки документов](../../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303 — 072_DocumentTabRedline")

 Используйте:
при создании пользовательского интерфейса, который должен соответствовать вкладкам документов и автоматически изменяться при обновлении тем или добавлении новых цветов темы.

 Не используйте:
для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.

#### <a name="open-document-tabs"></a>Вкладки открытых документов
 Каждый открытый документ имеет вкладку в канале вкладок документов, на которой показано его имя. Документы могут быть либо выбраны, либо открыты в фоновом режиме. На их вкладках указываются перечисленные ниже состояния.

- Выбранная вкладка представляет документ, который в настоящее время отображается в контейнере документа. Выбранная вкладка имеет границу документа, которая располагается по верхнему краю контейнера документа.

- Вкладки «фон» — это любые вкладки документов, не выбранные в данный момент. После нажатия они становятся выбранной вкладкой и получают все цвета фона, границы и текста из этих имен токенов.

  ![Красная линия открытой вкладки документов](../../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303 — 073_OpenDocumentTabRedline")

  Используйте:
  при создании пользовательских вкладок документов.

  Не используйте:
  - для временных вкладок (вкладок предварительного просмотра);

- для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.

#### <a name="selected-tab"></a>Выбранная вкладка
 **Focused**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Выбранная вкладка с фокусом ввода](../../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 — 074_SelectedTabFocused")

 **Выбранная вкладка документа, с фокусом ввода**

 Фон

 `Environment.FileTabSelectedGradientTop`

 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

 Передний план (текст)

 `Environment.FileTabSelectedText`

 Рамка

 `Environment.FileTabSelectedBorder`

 Цвет совпадает с цветом фона.

 Граница документа

 `Environment.FileTabDocumentBorderBackground`

 **Без фокуса ввода**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Выбранная вкладка без фокуса ввода](../../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 — 075_SelectedTabUnfocused")

 **Выбранная вкладка документа, без фокуса ввода**

 Фон

 `Environment.FileTabInactiveGradientTop`

 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

 Передний план (текст)

 `Environment.FileTabInactiveText`

 Рамка

 `Environment.FileTabInactiveBorder`

 Цвет совпадает с цветом фона.

 Граница документа

 `Environment.FileTabInactiveDocumentBorderBackground`

#### <a name="background-tab"></a>Вкладка фона
 **Default**

 ![Вкладка фона](../../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 — 076_BackgroundTab")

 **Вкладка фона по умолчанию**

 Фон

 `Environment.FileTabBackground`

 Передний план (текст)

 `Environment.FileTabText`

 Рамка

 `Environment.FileTabBorder`

 Цвет совпадает с цветом фона.

 **Наведение**

 ![Вкладка фона при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 — 077_BackgroundTabHover")

 **Вкладка фона при наведении курсора мыши**

 Фон

 `Environment.FileTabHotGradientTop`

 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

 Передний план (текст)

 `Environment.FileTabHotText`

 Рамка

 `Environment.FileTabHotBorder`

 Цвет совпадает с цветом фона.

#### <a name="preview-tab"></a>Вкладка предварительного просмотра

Вкладка предварительного просмотра отображается в правой части канала вкладок документов, когда пользователь щелкает элемент в окне инструментов обозревателя решений. Она служит для предварительного просмотра документа и дает пользователю возможность сохранять документ открытым в левой части канала вкладок документов. Одновременно может быть открыта только одна вкладка предварительного просмотра. Так же как открытые вкладки, вкладки предварительного просмотра имеют как фоновое, так и выбранное состояния и в активном состоянии могут получать фокус ввода и терять его.

![Красная линия вкладки предварительного просмотра](../../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303 — 078_PreviewTabRedline")

Используйте:
при создании временной области предварительного просмотра, если какой-либо элемент должен иметь цвет текущей вкладки предварительного просмотра.

Не используйте:
- для любого документа или вкладки, которая не является временной (не служит для предварительного просмотра);

- для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.

  **Выбранная вкладка предварительного просмотра с фокусом ввода**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Вкладка предварительного просмотра с фокусом ввода](../../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 — 079_PreviewTabFocused")

  **Вкладка предварительного просмотра с фокусом ввода**

  Фон

  `Environment.FileTabProvisionalSelectedActive`

  Передний план (текст)

  `Environment.FileTabProvisionalSelectedActiveForeground`

  Рамка

  `Environment.FileTabProvisionalSelectedActiveBorder`

  Цвет совпадает с цветом фона.

  Граница документа

  `Environment.FileTabProvisionalSelectedActiveBorder`

  **Выбранная вкладка предварительного просмотра без фокуса ввода**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Вкладка предварительного просмотра без фокуса ввода](../../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 — 080_PreviewTabUnfocused")

  **Вкладка предварительного просмотра без фокуса ввода**

  Фон

  `Environment.FileTabProvisionalSelectedInactive`

  Передний план (текст)

  `Environment.FileTabProvisionalSelectedInactiveForeground`

  Рамка

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  Граница документа

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  **Фоновая вкладка предварительного просмотра: по умолчанию**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Вкладка фона предварительного просмотра](../../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 — 081_PreviewBackgroundTab")

  **Фоновая вкладка предварительного просмотра**

  Фон

  `Environment.FileTabProvisionalInactive`

  Передний план (текст)

  `Environment.FileTabProvisionalInactiveForeground`

  Рамка

  `Environment.FileTabProvisionalInactiveBorder`

  Цвет совпадает с цветом фона.

  **Фоновая вкладка предварительного просмотра: при наведении указателя**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Вкладка фона предварительного просмотра при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 — 082_PreviewBackgroundTabHover")

  **Фоновая вкладка предварительного просмотра при наведении указателя**

  Фон

  `Environment.FileTabProvisionalHover`

  Передний план (текст)

  `Environment.FileTabProvisionalHoverForeground`

  Рамка

  `Environment.FileTabProvisionalHoverBorder`

  Цвет совпадает с цветом фона.

#### <a name="document-overflow-button"></a>Кнопка переполнения документа

Кнопка переполнения документа присутствует, если открыт один или несколько документов, вне зависимости от того, имеется ли в текущей конфигурации пространство по вертикали для размещения всех вкладок документов. В раскрывающемся меню переполнения документа, к которому применяются цвета **CommandBarMenu** (см. раздел [Menus](../../misc/shared-colors.md#BKMK_CommandMenus)), приводится список всех открытых документов, как видимых, так и скрытых. Глиф переполнения меняется в зависимости от того, отображаются ли все открытые документы в канале вкладок.

![Красная линия переполнения](../../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303 — 083_OverflowRedline")

Используйте:
при создании пользовательской кнопки переполнения документа.

Не используйте:
- для пользовательского интерфейса, отличного от кнопки переполнения;

- для кнопок переполнения панели команд.

  **Default**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Переполнение](../../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 — 084_Overflow")

  **Кнопка переполнения документа**

  Фон

  `Environment.DocWellOverflowButtonBackground`

  Передний план (глиф)

  `Environment.DocWellOverflowButtonGlyph`

  Рамка

  Н/Д

  **Наведение**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Переполнение при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 — 085_OverflowHover")

  **Кнопка переполнения документа при наведении указателя**

  Фон

  `Environment.DocWellOverflowButtonMouseOverBackground`

  Передний план (глиф)

  `Environment.DocWellOverflowButtonMouseOverGlyph`

  Рамка

  `Environment.DocWellOverflowButtonMouseOverBorder`

  **Pressed**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Активное переполнение](../../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 — 086_OverflowPressed")

  **Активная кнопка переполнения документа**

  Фон

  `Environment.DocWellOverflowButtonMouseDownBackground`

  Передний план (глиф)

  `Environment.DocWellOverflowButtonMouseDownGlyph`

  Рамка

  `Environment.DocWellOverflowButtonMouseDownBorder`

## <a name="tool-windows"></a>Окна инструментов
 Воссоздавать окна инструментов не нужно, так как они предоставляются средой Visual Studio. Однако может потребоваться использовать цвета, применяемые в окнах инструментов, чтобы ваш пользовательский интерфейс был согласован с этой частью среды Visual Studio.

 ![Красная линия окна инструментов](../../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303 — 087_ToolWindowRedline")

 Используйте:
при создании пользовательского интерфейса, соответствующего окнам инструментов.

 Не используйте:
для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.

### <a name="tool-window-frame"></a>Рамка окна инструментов
 Окна инструментов в Visual Studio используются для множества различных задач и могут иметь одно из нескольких состояний. Если окно инструментов открыто, оно может быть назначено одной из четырех сторон области документа. Окна инструментов также могут перемещаться за пределы интегрированной среды документов, что позволяет размещать их в любом месте экрана. Перемещаемые окна всегда находятся поверх интегрированной среды разработки. Наконец, окна инструментов могут закрепляться как окна документов и отображаться в виде вкладок в контейнере документа. К окнам инструментов, закрепленным как окна документов, частично применяются имена токенов окна документа.

 ![Красная линия кадра окна инструментов](../../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303 — 088_ToolWindowFrameRedline")

 Используйте:
при создании пользовательского интерфейса, соответствующего окнам инструментов.

 Не используйте:
для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.

 **Закрепить**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Закрепленное окно инструментов](../../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 — 089_ToolWindowDocked")

 Фон

 `Environment.ToolWindowBackground`

 Рамка

 `Environment.ToolWindowBorder`

 **Перемещаемое: с фокусом ввода**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Окно инструментов в фокусе](../../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 — 090_ToolWindowFocused")

 Фон

 `Environment.ToolWindowBackground`

 Рамка

 `Environment.MainWindowActiveDefaultBorder`

 **Перемещаемое: без фокуса ввода**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Окно инструментов не в фокусе](../../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 — 091_ToolWindowUnfocused")

 Фон

 `Environment.ToolWindowBackground`

 Рамка

 `Environment.MainWindowInactiveBorder`

### <a name="tool-window-title-bar"></a>Заголовок окна инструментов
 Граница заголовка окна является, по сути, не границей, а толстой линией по верхнему краю заголовка. Она не имеет имени токена для состояния без фокуса ввода.

 ![Красная линия панели заголовка окна инструментов](../../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303 — 092_ToolWindowTitleBarRedline")

 Используйте:
при создании пользовательского интерфейса, соответствующего окнам инструментов.

 Не используйте:
для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.

 **Focused**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Панель заголовка в фокусе](../../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 — 093_TitleBarFocused")

 **Заголовок окна с фокусом ввода**

 Фон

 `Environment.TitleBarActiveGradientBegin`

 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

 Передний план (текст)

 `Environment.TitleBarActiveText`

 Рамка

 `Environment.TitleBarActiveBorder`

 Цвет совпадает с цветом фона.

 Маркер перетаскивания

 `Environment.TitleBarDragHandleActive`

 **Без фокуса ввода**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Панель заголовка без фокуса ввода](../../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 — 094_TitleBarUnfocused")

 **Заголовок окна без фокуса ввода**

 Фон

 `Environment.TitleBarInactiveGradientBegin`

 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

 Передний план (текст)

 `Environment.TitleBarInactiveText`

 Рамка

 Н/Д

 Маркер перетаскивания

 `Environment.TitleBarDragHandle`

#### <a name="title-bar-buttons"></a>Кнопки в заголовке окна

![Красная линия кнопки панели заголовка](../../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303 — 095_TitleBarButtonRedline")

Используйте:
для кнопок в пользовательском интерфейсе, для которых используются токены цветов, связанные с заголовками окон инструментов.

Не используйте:
- для кнопок, отображаемых в других местах;

- в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.

  **Default**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Кнопка панели заголовка с фокусом ввода](../../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 — 096_TitleBarButtonFocused")

  **Focused**

  Фон

  Н/Д

  Передний план (глиф)

  `Environment.ToolWindowButtonActiveGlyph`

  Рамка

  Н/Д

  ![Кнопка панели заголовка без фокуса ввода](../../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 — 097_TitleBarButtonUnfocused")

  **Без фокуса ввода**

  Фон

  Н/Д

  Передний план (глиф)

  `Environment.ToolWindowButtonInactiveGlyph`

  Рамка

  Н/Д

  **Наведение**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Кнопка панели заголовка с фокусом ввода при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 — 098_TitleBarButtonFocusedHover")

  **Focused**

  Фон

  `Environment.ToolWindowButtonHoverActive`

  Передний план (глиф)

  `Environment.ToolWindowButtonHoverActiveGlyph`

  Рамка

  `Environment.ToolWindowButtonHoverActiveBorder`

  ![Кнопка панели заголовка без фокуса ввода при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 — 099_TitleBarButtonUnfocusedHover")

  **Без фокуса ввода**

  Фон

  `Environment.ToolWindowButtonHoverInactive`

  Передний план (глиф)

  `Environment.ToolWindowButtonHoverInactiveGlyph`

  Рамка

  `Environment.ToolWindowButtonHoverInactiveBorder`

  **Pressed**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Активная кнопка панели заголовка с фокусом ввода](../../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 — 100_TitleBarButtonFocusedPressed")

  **Focused**

  Фон

  `Environment.ToolWindowButtonDown`

  Передний план (глиф)

  `Environment.ToolWindowButtonDownActiveGlyph`

  Рамка

  `Environment.ToolWindowButtonDownBorder`

  ![Активная кнопка панели заголовка без фокуса ввода](../../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 — 101_TitleBarButtonUnfocusedPressed")

  **Без фокуса ввода**

  Фон

  `Environment.ToolWindowButtonDown`

  Передний план (глиф)

  `Environment.ToolWindowButtonDownInactiveGlyph`

  Рамка

  `Environment.ToolWindowButtonDownBorder`

### <a name="tool-window-tabs"></a>Вкладки окна инструментов
 ![Красная линия вкладки окна инструментов](../../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303 — 102_ToolWindowTabRedline")

 Используйте:
при создании пользовательского интерфейса, соответствующего окнам инструментов.

 Не используйте:
для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.

 **Выбранная вкладка**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Вкладка окна инструментов с фокусом ввода](../../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 — 103_ToolWindowTabFocused")

 **Выбранная вкладка окна инструментов с фокусом ввода**

 Фон

 `Environment.ToolWindowTabSelectedTab`

 Передний план (текст)

 `Environment.ToolWindowTabSelectedActiveText`

 Рамка

 `Environment.ToolWindowTabSelectedBorder`

 Цвет совпадает с цветом фона.

 Компонент

 Элемент

 Имя токена: Category.color

 ![Вкладка окна инструментов без фокуса ввода](../../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 — 104_ToolWindowTabUnfocused")

 **Выбранная вкладка окна инструментов без фокуса ввода**

 Фон

 `Environment.ToolWindowTabSelectedTab`

 Передний план (текст)

 `Environment.ToolWindowTabSelectedText`

 Рамка

 `Environment.ToolWindowTabSelectedBorder`

 Цвет совпадает с цветом фона.

 **Вкладка фона**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Вкладка фона окна инструментов](../../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 — 105_ToolWindowBackgroundTab")

 **Фоновая вкладка окна инструментов**

 Фон

 `Environment.ToolWindowTabGradientBegin`

 Ограничения градиента устанавливаются в Visual Studio 2013 в то же значение цвета.

 `Environment.ToolWindowTabGradientEnd`

 Ограничения градиента устанавливаются в Visual Studio 2013 в то же значение цвета.

 Передний план (текст)

 `Environment.ToolWindowTabText`

 Рамка

 `Environment.ToolWindowTabBorder`

 Компонент

 Элемент

 Имя токена: Category.color

 ![Вкладка фона окна инструментов при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 — 106_ToolWindowBackgroundTabHover")

 **Фоновая вкладка окна инструментов при наведении указателя**

 Фон

 `Environment.ToolWindowTabMouseOverBackgroundBegin`

 Ограничения градиента устанавливаются в Visual Studio 2013 в то же значение цвета.

 `Environment.ToolWindowTabMouseOverBackgroundEnd`

 Ограничения градиента устанавливаются в Visual Studio 2013 в то же значение цвета.

 Передний план (текст)

 `Environment.ToolWindowTabMouseOverText`

 Рамка

 `Environment.ToolWindowTabMouseOverBorder`

 Цвет совпадает с цветом фона.

### <a name="auto-hide-tabs"></a>Автоматически скрываемые вкладки
 ![Автоматически&#45;скрыть красная линия](../../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303 — 107_AutoHideRedline")

 Используйте:
при создании пользовательского интерфейса, соответствующего автоматически скрываемым вкладкам окна инструментов.

 Не используйте:
для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.

 **Default**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Автоматически&#45;вкладка "скрыть"](../../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 — 108_AutoHideTab")

 **Автоматически скрываемая вкладка по умолчанию**

 Фон

 `Environment.AutoHideTabBackgroundBegin`

 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

 Передний план (текст)

 `Environment.AutoHideTabText`

 Рамка

 `Environment.AutoHideTabBorder`

 **Наведение**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Автоматически&#45;скрывать табуляцию при наведении указателя](../../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 — 109_AutoHideTabHover")

 **Вкладка автоматического скрытия при наведении курсора мыши**

 Фон

 `Environment.AutoHideTabMouseOverBackgroundBegin`

 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

 Передний план (текст)

 `Environment.AutoHideTabMouseOverText`

 Рамка

 `Environment.AutoHideTabMouseOverBorder`

## <a name="common-shared-controls"></a>Стандартные общие элементы управления
 При использовании в компоненте стандартной панели команд Visual Studio вы имеете доступ к оформленным элементам управления оболочки. Изменять шаблон этих стандартных элементов управления не следует. Однако если вам нужно создать пользовательскую панель команд, вам также может потребоваться создать пользовательские элементы управления. В этом случае используйте правильные имена токенов для каждого из указанных ниже элементов управления, чтобы ваш пользовательский интерфейс был согласован с остальной средой Visual Studio.

### <a name="search-box"></a>Поле поиска
 По возможности используйте стандартный элемент управления поиском, предоставляемый средой Visual Studio. Цвета поля поиска находятся в категории SearchControl в файле **ShellColors.pkgdef** , который содержит имена токенов для поля ввода, управляющей кнопки, кнопки раскрывающегося списка и раскрывающегося меню.

 Поле поиска может находиться в одном из нескольких состояний. Некоторые из них взаимоисключающие.

- "С фокусом ввода" или "без фокуса ввода" указывает на то, находится ли курсор в текстовом поле.

- "Активно" или "неактивно" указывает на то, ввел ли пользователь запрос в текстовом поле.

- "При наведении указателя" означает, что пользователь навел указатель мыши на поле поиска (это состояние переопределяет все остальные).

- "Отключено" означает, что функция поиска в текущем контексте отключена.

  ![Красная линия окна поиска](../../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303 — 110_SearchBoxRedline")

  Используйте:
  при разработке пользовательского поля поиска.

  Не используйте:
  - для любого элемента, не являющегося полем поиска;

- для любого элемента, который не должен всегда соответствовать пользовательскому интерфейсу поля поиска.

  **Focused**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Поле ввода окна поиска с фокусом ввода](../../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 — 111_SearchInputFieldFocused")

  **Поле ввода**

  Фон

  `SearchControl.FocusedBackground`

  Передний план (текст)

  `SearchControl.FocusedBackground`

  Рамка

  `SearchControl.FocusedBorder`

  Separator

  `SearchControl.FocusedDropDownSeparator`

  ![Кнопка поиска с фокусом ввода](../../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 — 112_SearchActionButtonFocused")

  **Кнопка действия**

  Фон

  None

  Передний план (глиф поиска)

  `SearchControl.SearchGlyph`

  Передний план (глиф остановки)

  `SearchControl.StopGlyph`

  Передний план (глиф очистки)

  `SearchControl.ClearGlyph`

  Рамка

  Н/Д

  ![Кнопка "&#45;", направленная вниз](../../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 — 113_SearchDropdownButtonFocused")

  **Кнопка раскрывающегося списка**

  Фон

  `SearchControl.FocusedDropDownButton`

  Передний план (глиф)

  `SearchControl.FocusedDropDownButtonGlyph`

  Рамка

  `SearchControl.FocusedDropDownButtonBorder`

  **Без фокуса ввода**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Поле ввода окна поиска без фокуса ввода](../../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 — 114_SearchInputFieldUnfocused")

  **Активное поле ввода**

  Фон

  `SearchControl.SearchActiveBackground`

  Передний план (текст)

  `SearchControl.SearchActiveBackground`

  Рамка

  `SearchControl.UnfocusedBorder`

  Separator

  `SearchControl.DropDownSeparator`

  ![Неактивное поле ввода окна поиска без фокуса ввода](../../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")

  **Неактивное поле ввода**

  Фон

  `SearchControl.Unfocused`

  Передний план (текст)

  `SearchControl.Unfocused`

  Рамка

  `SearchControl.UnfocusedBorder`

  Separator

  `SearchControl.DropDownSeparator`

  ![Кнопка поиска без фокуса ввода](../../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 — 115_SearchActionButtonUnfocused")

  **Кнопка действия**

  Фон

  Н/Д

  Передний план (глиф поиска)

  `SearchControl.SearchGlyph`

  Передний план (глиф остановки)

  `SearchControl.StopGlyph`

  Передний план (глиф очистки)

  `SearchControl.ClearGlyph`

  Рамка

  Н/Д

  ![Кнопка "Удалить"&#45;"вниз" нефокусна](../../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 — 116_SearchDropdownButtonUnfocused")

  **Кнопка раскрывающегося списка**

  Фон

  `SearchControl.UnfocusedDropDownButton`

  Передний план (глиф)

  `SearchControl.UnfocusedDropDownButtonGlyph`

  Рамка

  `SearchControl.UnfocusedDropDownButtonBorder`

  **Pressed**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Активная кнопка поиска](../../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")

  **Кнопка действия**

  Фон

  `SearchControl.ActionButtonMouseDown`

  Передний план (глиф)

  `SearchControl.ActionButtonMouseDownGlyph`

  Рамка

  `SearchControl.ActionButtonMouseDownBorder`

  ![Кнопка "Удалить"&#45;нажатии кнопки вниз](../../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")

  **Кнопка раскрывающегося списка**

  Фон

  `SearchControl.MouseDownDropDownButton`

  Передний план (глиф)

  `SearchControl.MouseDownDropDownButtonGlyph`

  Рамка

  `SearchControl.MouseDownDropDownButtonBorder`

  **Выделено (только текст)**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Выделение поля ввода окна поиска](../../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 — 120_SearchInputFieldHighlight")

  **Поле ввода с выделенным текстом**

  Фон

  `SearchControl.Selection`

  Передний план (текст)

  `SearchControl.FocusedBackground`

  Рамка

  None

  Separator

  `SearchControl.FocusedDropDownSeparator`

  **Отключен**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Неактивное поле ввода окна поиска](../../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 — 121_SearchInputFieldDisabled")

  **Поле ввода**

  Фон

  `SearchControl.Disabled`

  Передний план (текст)

  `SearchControl.Disabled`

  Рамка

  `SearchControl.DisabledBorder`

  Separator

  `SearchControl.DropDownSeparator`

  ![Неактивная кнопка поиска](../../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 — 122_SearchActionButtonDisabled")

  **Кнопка действия**

  Фон

  None

  Передний план (глиф)

  `SearchControl.ActionButtonDisabledGlyph`

  Рамка

  None

  ![Кнопка "Удалить"&#45;"вниз" отключена](../../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 — 123_SearchDropdownButtonDisabled")

  **Кнопка раскрывающегося списка**

  Фон

  None

  Передний план (глиф)

  `SearchControl.DisabledDownButtonGlyph`

  Рамка

  None

#### <a name="search-drop-down-lists"></a>Раскрывающиеся списки поиска

Раскрывающиеся меню в поле поиска могут быть немного более сложными, чем другие раскрывающиеся меню в Visual Studio. Разделы "предлагаемые запросы поиска" и "параметры поиска" могут присутствовать в меню вместе или по отдельности. Каждый из них имеет особые цвета. Если имеются оба этих раздела, они разделяются линией, а все раскрывающееся меню окружено границей.

![Поиск&#45;вниз красная линия](../../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303 — 124_SearchDropdownRedline")

Используйте:
- при создании пользовательского раскрывающегося списка поиска;

- правильные имена токенов для соответствующих компонентов списка.

  Не используйте:
  - для раскрывающихся списков, которые используются в других контекстах;

- в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.

  **По умолчанию (нет других состояний)**

  Элемент

  Имя токена: Category.color

  Рамка

  `SearchControl.PopupBorder`

  Separator

  `SearchControl.PopupSectionHeaderSeparator`

  Shadow

  `Environment.DropShadowBackground`

  **Default**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Предлагаемый поиск](../../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 — 125_SearchSuggested")

  **Предлагаемые запросы поиска**

  Фон

  `SearchControl.PopupItemsListBackgroundGradientBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст)

  `SearchControl.PopupItemText`

  ![Флажок поиска](../../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 — 126_SearchCheckbox")

  **Параметры поиска (флажок)**

  ![Параметры поиска](../../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 — 127_SearchOptions")

  **Параметры поиска (ссылка)**

  Фон

  `SearchControl.PopupSectionBackgroundGradientBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст флажка)

  `SearchControl.PopupCheckboxText`

  Передний план (текст ссылки)

  `SearchControl.PopupButtonText`

  Фон заголовка

  `SearchControl.PopupSectionHeaderGradientBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст заголовка)

  `SearchControl.PopupSectionHeaderText`

  **Наведение**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Предлагаемый поиск при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 — 128_SearchSuggestedHover")

  **Предлагаемые запросы поиска**

  Фон

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст)

  `SearchControl.PopupMouseOverItemText`

  Рамка

  `SearchControl.PopupControlMouseOverBorder`

  ![Флажок поиска при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 — 129_SearchCheckboxHover")

  **Предлагаемые запросы поиска (флажок)**

  ![Параметры поиска при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 — 130_SearchOptionsHover")

  **Параметры поиска**

  Фон

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст флажка)

  `SearchControl.PopupCheckboxMouseDownText`

  Передний план (текст ссылки)

  `SearchControl.PopupButtonMouseDownText`

  Рамка

  `SearchControl.PopupControlMouseOverBorder`

  **Pressed**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Активный предлагаемый поиск](../../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 — 131_SearchSuggestedPressed")

  **Предлагаемые запросы поиска (флажок)**

  ![Активные параметры поиска](../../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 — 132_SearchOptionsPressed")

  **Параметры поиска**

  Фон флажка

  `SearchControl.PopupControlMouseDownBackgroundGradientBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  `SearchControl.PopupControlMouseDownBackgroundGradientEnd`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст флажка)

  `SearchControl.PopupCheckboxMouseDownText`

  Фон ссылки

  `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`

  Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.

  Передний план (текст ссылки)

  `SearchControl.PopupButtonMouseDownText`

### <a name="hyperlink"></a>Гиперссылка
 Гиперссылка — это один из элементов управления, для которого нет пары цветов переднего плана и фона. Во всех случаях используйте основной цвет гиперссылки, который будет правильно отображаться на темном, сером и белом фоне. Если вы не используете токен цвета для элемента управления "гиперссылка", то будет применяться системный цвет по умолчанию для состояния "активно", то есть гиперссылка будет мигать красным. Это означает, что для элемента управления используется неправильный токен цвета среды.

 ![Красная линия гиперссылки](../../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303 — 133_HyperlinkRedline")

 Используйте:
если нужно создать пользовательскую гиперссылку.

 Не используйте:
для любого элемента, не являющегося гиперссылкой.

 **Default**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Гиперссылка по умолчанию](../../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303 — 134_Hyperlink")

 Передний план (текст)

 `Environment.PanelHyperlink`

 **Наведение**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Гиперссылка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303 — 135_HyperlinkHover")

 Передний план (текст)

 `Environment.PanelHyperlinkHover`

 **Pressed**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Активная гиперссылка](../../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303 — 136_HyperlinkPressed")

 Передний план (текст)

 `Environment.PanelHyperlinkPressed`

 **Отключен**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Неактивная гиперссылка](../../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303 — 137_HyperlinkDisabled")

 Передний план (текст)

 `Environment.PanelHyperlinkDisabled`

### <a name="infobar"></a>Информационная панель
 Информационные панели служат для предоставления дополнительной информации о данном контексте и всегда отображаются в верхней части окна документа или окна инструментов.

 ![Красная линия информационной панели](../../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303 — 138_InfobarRedline")

 Используйте:
при создании пользовательских информационных панелей.

 Не используйте:
для элементов пользовательского интерфейса, которые не похожи на информационную панель.

 Компонент

 Элемент

 Имя токена: Category.color

 ![Информационная панель](../../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 — 139_Infobar")

 **Информационная панель**

 Фон

 `Environment.InfoBackground`

 Передний план (текст)

 `Environment.InfoText`

 Рамка

 `Environment.ToolWindowBorder`

### <a name="scroll-bar"></a>полоса прокрутки;
 Полосы прокрутки оформляются средой Visual Studio, и применять к ним темы не нужно. Однако вы можете решить, что вы хотите использовать цвета, используемые в полосах прокрутки, чтобы пользовательский интерфейс всегда соответствовал этой части среды Visual Studio.

 ![Красная линия полосы прокрутки](../../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303 — 140_ScrollbarRedline")

 Используйте:
при создании пользовательского интерфейса, который должен соответствовать полосам прокрутки Visual Studio.

 Не используйте... для чего вы не хотите всегда сопоставлять пользовательский интерфейс ScrollBar.

 **Default**

 Компонент

 Элемент

 Имя токена: Category.color

 ![полоса прокрутки;](../../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 — 141_Scrollbar")

 **Элемента**

 Полоса прокрутки

 `Environment.ScrollBarBackground`

 Передний план (бегунок)

 `Environment.ScrollBarThumbBackground`

 ![Стрелки полосы прокрутки](../../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 — 142_ScrollbarArrow")

 **Стрелка прокрутки**

 Фон

 `Environment.ScrollBarArrowBackground`

 Цвет совпадает с цветом полосы прокрутки.

 Передний план (глиф)

 `Environment.ScrollBarArrowGlyph`

 **Наведение**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Полоса прокрутки при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 — 143_ScrollbarHover")

 **Элемента**

 Полоса прокрутки

 `Environment.ScrollBarBackground`

 Передний план (бегунок)

 `Environment.ScrollBarThumbMouseOverBackground`

 ![Стрелки полосы прокрутки при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 — 144_ScrollbarArrowHover")

 **Стрелка прокрутки**

 Фон

 `Environment.ScrollBarArrowMouseOverBackground`

 Цвет совпадает с цветом полосы прокрутки.

 Передний план (глиф)

 `Environment.ScrollBarArrowGlyphMouseOver`

 **Pressed**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Активная полоса прокрутки](../../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 — 145_ScrollbarPressed")

 **Элемента**

 Полоса прокрутки

 `Environment.ScrollBarBackground`

 Передний план (бегунок)

 `Environment.ScrollBarThumbPressedBackground`

 ![Активные стрелки полосы прокрутки](../../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 — 146_ScrollbarArrowPressed")

 **Стрелка прокрутки**

 Фон

 `Environment.ScrollBarArrowPressedBackground`

 Цвет совпадает с цветом полосы прокрутки.

 Передний план (глиф)

 `Environment.ScrollBarArrowGlyphPressed`

### <a name="tree-view"></a><a name="BKMK_TreeView"></a> Представление в виде дерева

В некоторых окнах инструментов, включая обозреватель решений, обозреватель сервера и представление классов, реализована иерархическая организационная схема, цвета которой определяются названиями цветов в категории TreeView. Все элементы в иерархическом представлении имеют цвета фона и текста. Элементы с вложенными дочерними элементами также имеют глифы, которые указывают на то, является ли элемент свернутым или развернутым.

![Красная линия представления в виде дерева](../../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303 — 147_TreeViewRedline")

Используйте:
если необходимо реализовать иерархическое представление.

Не используйте:
- для каких-либо элементов, отличных от иерархического представления;

- в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.

  **Default**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Представление в виде дерева](../../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 — 148_TreeView")

  Фон

  `TreeView.Background`

  Передний план (текст)

  `TreeView.Background`

  Передний план (глиф)

  `TreeView.Glyph`

  Рамка

  None

  **Наведение**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Представление в виде дерева при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 — 149_TreeViewHover")

  Фон

  `TreeView.Background`

  Передний план (текст)

  `TreeView.Background`

  Передний план (глиф)

  `TreeView.GlyphMouseOver`

  Рамка

  None

  **Перетаскивание**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Перетаскивание иерархического представления](../../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 — 150_TreeViewDragOver")

  Фон

  `TreeView.DragOverItem`

  Передний план (текст)

  `TreeView.DragOverItem`

  Передний план (глиф)

  `TreeView.DragOverItemGlyph`

  Рамка

  None

  **Selected**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Иерархическое представление в фокусе](../../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 — 151_TreeViewFocused")

  **Focused**

  Фон

  `TreeView.SelectedItemActive`

  Передний план (текст)

  `TreeView.SelectedItemActive`

  Передний план (глиф)

  `TreeView.SelectedItemActiveGlyph`

  Рамка

  `TreeView.FocusVisualBorder`

  ![Представление в виде дерева в фокусе](../../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 — 152_TreeViewUnfocused")

  **Без фокуса ввода**

  Фон

  `TreeView.SelectedItemInactive`

  Передний план (текст)

  `TreeView.SelectedItemInactive`

  Передний план (глиф)

  `TreeView.SelectedItemInactiveGlyph`

  Рамка

  None

  **Наведение указателя на выделенный элемент**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Представление в виде дерева в фокусе при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 — 153_TreeViewFocusedHover")

  **Focused**

  Фон

  `TreeView.SelectedItemActive`

  Передний план (текст)

  `TreeView.SelectedItemActive`

  Передний план (глиф)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Рамка

  Нет`TreeView.FocusVisualBorder`

  ![Иерархическое представление не в фокусе при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 — 154_TreeViewUnfocusedHover")

  **Без фокуса ввода**

  Фон

  `TreeView.SelectedItemInactive`

  Передний план (текст)

  `TreeView.SelectedItemInactive`

  Передний план (глиф)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Рамка

  None

### <a name="button-controls"></a>Элементы управления "Кнопка"
 ![Красная линия элемента управления "Кнопка"](../../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303 — 155_ButtonControlRedline")

 Используйте:
для кнопок в контейнере документа, которые должны интегрироваться с темами Visual Studio (светлая, темная, синяя или системная высококонтрастная тема).

 Не используйте:
для кнопок, которые будут отображаться на пользовательском фоне, не входящем в тему Visual Studio.

 **Default**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Кнопка](../../extensibility/ux-guidelines/media/0303-156-button.png "0303 — 156_Button")

 Кнопка

 `CommonControls.Button`

 Граница кнопки

 `CommonControls.ButtonBorder`

 **Отключен**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Неактивна кнопка](../../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 — 157_ButtonDisabled")

 Кнопка

 `CommonControls.ButtonDisabled`

 Граница кнопки

 `CommonControls.ButtonBorderDisabled`

 **Наведение**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Кнопка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 — 158_ButtonHover")

 Кнопка

 `CommonControls.ButtonHover`

 Граница кнопки

 `CommonControls.ButtonBorderHover`

 **Pressed**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Активная кнопка](../../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 — 159_ButtonPressed")

 Кнопка

 `CommonControls.ButtonPressed`

 Граница кнопки

 `CommonControls.ButtonBorderPressed`

 **Focused**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Кнопка в фокусе](../../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 — 160_ButtonFocused")

 Кнопка

 `CommonControls.ButtonFocused`

 Граница кнопки

 `CommonControls.ButtonBorderFocused`

### <a name="check-box-controls"></a>Элементы управления "Флажок"
 ![Красная линия флажка](../../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303 — 161_CheckboxRedline")

 Используйте:
для элементов управления типа "Флажок", содержащихся в контейнере документа.

 Не используйте:
для пользовательского интерфейса, который не является элементом управления "Флажок".

 **Default**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Флажок](../../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 — 162_Checkbox")

 Фон

 `CommonControls.CheckBoxBackground`

 Рамка

 `CommonControls.CheckBoxBorder`

 Текст

 `CommonControls.CheckBoxText`

 Глиф

 `CommonControls.CheckBoxGlyph`

 **Отключен**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Неактивный флажок](../../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 — 163_CheckboxDisabled")

 Фон

 `CommonControls.CheckBoxBackgroundDisabled`

 Рамка

 `CommonControls.CheckBoxBorderDisabled`

 Текст

 `CommonControls.CheckBoxTextDisabled`

 Глиф

 `CommonControls.CheckBoxGlyphDisabled`

 **Наведение**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Флажок при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 — 164_CheckboxHover")

 Фон

 `CommonControls.CheckBoxBackgroundHover`

 Рамка

 `CommonControls.CheckBoxBorderHover`

 Текст

 `CommonControls.CheckBoxTextHover`

 Глиф

 `CommonControls.CheckBoxGlyphHover`

 **Pressed**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Активный флажок](../../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 — 165_CheckboxPressed")

 Фон

 `CommonControls.CheckBoxBackgroundPressed`

 Рамка

 `CommonControls.CheckBoxBorderPressed`

 Текст

 `CommonControls.CheckBoxTextPressed`

 Глиф

 `CommonControls.CheckBoxGlyphPressed`

 **Focused**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Флажок с фокусом ввода](../../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 — 166_CheckboxFocused")

 Фон

 `CommonControls.CheckBoxBackgroundFocused`

 Рамка

 `CommonControls.CheckBoxBorderFocused`

 Текст

 `CommonControls.CheckBoxTextFocused`

 Глиф

 `CommonControls.CheckBoxGlyphFocused`

### <a name="drop-boxcombo-box-controls"></a>Элементы управления "Раскрывающийся список" и "Поле со списком"

![Drop&#45;&#47;поле со списком красная линия](../../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303 — 167_DropDownComboBoxRedline")

Используйте:
для раскрывающихся списков и полей со списком, которые являются частью контейнера документа.

Не используйте:
- для других элементов пользовательского интерфейса, не являющихся раскрывающимися списками или полями со списком;

- для [Drop-down](../../misc/shared-colors.md#BKMK_CommandDropDown) или [Combo box](../../misc/shared-colors.md#BKMK_CommandComboBox) на панели команд.

  **Default**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Удалить&#45;вниз&#47;поле со списком](../../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 — 168_DropDownComboBox")

  Фон

  `CommonControls.ComboBoxBackground`

  Рамка

  `CommonControls.ComboBoxBorder`

  Текст

  `CommonControls.ComboBoxText`

  Separator

  `CommonControls.ComboBoxSeparator`

  Глиф

  `CommonControls.ComboBoxGlyph`

  Фон глифа

  `CommonControls.ComboBoxGlyphBackground`

  **Отключен**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Drop&#45;&#47;поле со списком отключено](../../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 — 169_DropDownComboBoxDisabled")

  Фон

  `CommonControls.ComboBoxBackgroundDisabled`

  Рамка

  `CommonControls.ComboBoxBorderDisabled`

  Текст

  `CommonControls.ComboBoxTextDisabled`

  Separator

  `CommonControls.ComboBoxSeparatorDisabled`

  Глиф

  `CommonControls.ComboBoxGlyphDisabled`

  Фон глифа

  `CommonControls.ComboBoxGlyphBackgroundDisabled`

  **Наведение**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Drop&#45;&#47;поле со списком при наведении указателя](../../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 — 170_DropDownComboBoxHover")

  Фон

  `CommonControls.ComboBoxBackgroundHover`

  Рамка

  `CommonControls.ComboBoxBorderHover`

  Текст

  `CommonControls.ComboBoxTextHover`

  Separator

  `CommonControls.ComboBoxSeparatorHover`

  Глиф

  `CommonControls.ComboBoxGlyphHover`

  Фон глифа

  `CommonControls.ComboBoxGlyphBackgroundHover`

  **Pressed**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Удалить&#45;вниз&#47;нажатии поля со списком](../../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 — 171_DropDownComboBoxPressed")

  Фон

  `CommonControls.ComboBoxBackgroundPressed`

  Рамка

  `CommonControls.ComboBoxBorderPressed`

  Текст

  `CommonControls.ComboBoxTextPressed`

  Separator

  `CommonControls.ComboBoxSeparatorPressed`

  Глиф

  `CommonControls.ComboBoxGlyphPressed`

  Фон глифа

  `CommonControls.ComboBoxGlyphBackgroundPressed`

  **Focused**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Перетащите&#45;вниз&#47;поле со списком](../../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 — 172_DropDownComboBoxFocused")

  Фон

  `CommonControls.ComboBoxBackgroundFocused`

  Рамка

  `CommonControls.ComboBoxBorderFocused`

  Текст

  `CommonControls.ComboBoxTextFocused`

  Separator

  `CommonControls.ComboBoxSeparatorFocused`

  Глиф

  `CommonControls.ComboBoxGlyphFocused`

  Фон глифа

  `CommonControls.ComboBoxGlyphBackgroundFocused`

  **Выделение текста в поле ввода**

  Компонент

  Элемент

  Имя токена: Category.color

  ![Перетащите&#45;вниз&#47;поле со списком ввод текста](../../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303 — 173_DropDownComboBoxTextInput")

  Выделить

  `CommonControls.ComboBoxTextInputSelection`

  **Активный — представление элемента списка**

  ![Перетащите&#45;вниз&#47;поле со списком в виде списка](../../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")

  Фон

  `CommonControls.ComboBoxListBackground`

  `CommonControls.ComboBoxListBackgroundHover`

  `CommonControls.ComboBoxListItemBackgroundPressed`

  `CommonControls.ComboBoxListItemBackgroundFocused`

  Рамка

  `CommonControls.ComboBoxListBorder`

  `CommonControls.ComboBoxListBorderHover`

  `CommonControls.ComboBoxListBorderPressed`

  `CommonControls.ComboBoxListBorderFocused`

  Текст элемента

  `CommonControls.ComboBoxListItemText`

  `CommonControls.ComboBoxListItemTextHover`

  `CommonControls.ComboBoxListItemTextPressed`

  `CommonControls.ComboBoxListItemTextFocused`

  Фон с тенью

  `CommonControls.ComboBoxListBackgroundShadow`

### <a name="tabular-data-grid-controls"></a>Табличные элементы управления данными (сетка)
 Табличные элементы управления данными, также называемые элементами управления "Сетка", — это стандартные элементы управления Visual Studio, которые можно использовать для представления больших объемов данных в нескольких столбцах. Стандартные табличные элементы управления данными встречаются в Visual Studio в нескольких местах: в окне инструментов "Список ошибок", в отчетах IntelliTrace, в представлении кучи памяти и т. д. Всегда используйте стандартные табличные элементы управления данными. Однако в некоторых редких случаях доступ к стандартным табличным элементам управления данными может отсутствовать. В таких ситуациях используйте указанные ниже имена токенов для обеспечения согласованности пользовательского интерфейса с другими табличными элементами управления данными в Visual Studio.

 ![Табличные данные &#40;элементе управления Grid&#41; красная линия](../../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303 — 197_TabularDataGridControlRedline")

 Используйте:
для табличных элементов управления или элементов управления "Сетка".

 Не используйте:
для элементов пользовательского интерфейса, которые не являются табличными элементами управления или элементами управления "Сетка".

#### <a name="column-headers"></a>Заголовки столбцов
 Заголовки столбцов состоят из фона, границы, текста заголовка и необязательного глифа, который обычно используется при сортировке сетки по данному столбцу.

 Состояние

 Элемент

 Имя токена: Category.color

 По умолчанию

 Фон

 `Header.Default`

 Передний план (текст)

 `Environment.CommandBarTextActive`

 Передний план (глиф)

 `Header.Glyph`

 Рамка

 `Header.SeparatorLine`

 Наведение

 Фон

 `Header.MouseOver`

 Передний план (текст)

 `Environment.CommandBarTextHover`

 Передний план (глиф)

 `Header.MouseOverGlyph`

 Рамка

 `Header.SeparatorLine`

 Нажато

 Фон

 `CommonControls.CheckBoxBackgroundPressed`

 Передний план (текст)

 `CommonControls.CheckBoxBorderPressed`

 Передний план (глиф)

 `CommonControls.CheckBoxTextPressed`

 Рамка

 `CommonControls.CheckBoxGlyphPressed`

#### <a name="list-view-items"></a>Элементы представления списка
 Элементы представления списка состоят из фона и содержимого. Содержимым может быть текст, значок или и то и другое.

 Состояние

 Элемент

 Имя токена: Category.color

 По умолчанию

 Фон

 Прозрачный

 Передний план (текст)

 `Environment.CommandBarTextActive`

 Рамка

 None

 Выбран (активен)

 Фон

 `TreeView.SelectedItemActive`

 Передний план (текст)

 `TreeView.SelectedItemActiveText`

 Рамка

 None

 Выбран (неактивен)

 Фон

 `TreeView.SelectedItemInactive`

 Передний план (текст)

 `TreeView.SelectedItemInactiveText`

 Рамка

 None

## <a name="manifest-designer"></a>Конструктор манифеста

Конструктор манифеста призван упростить редактирование файла манифеста в проектах Windows 8 и Windows Phone 8. Хотя общего готового шаблона нет, рекомендуется обеспечивать соответствие макету и цветам вкладок ориентации и навигации, а также общей структуре. Дополнительные сведения о макете см. в разделе [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Красная линия конструктора манифеста](../../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303 — 175_ManifestDesignerRedline")

Используйте:
- для конструкторов, которые похожи на конструктор манифеста;

- вместо использования стандартных элементов управления типа "Вкладка" в верхней части редактора в контейнере документа.

Не используйте:
- при наличии более чем шести вкладок;

- для пользовательского интерфейса, который отличается структурой от конструктора манифеста.

  Состояние

  Компонент

  Элемент

  Имя токена: Category.color

  По умолчанию (выбрано)

  Вкладка

  Фон

  `ManifestDesigner.TabActive`

  Рамка

  None

  Панель описания

  Фон

  `ManifestDesigner.DescriptionPane`

  Страница содержимого

  Фон

  `ManifestDesigner.Background`

  Текст подсказки для диалогового окна

  `ManifestDesigner.WatermarkText`

  Это имя токена не соответствует его функции.

  Не выбрано

  Вкладка

  Фон

  `ManifestDesigner.Tab.Inactive`

  Наведение

  Вкладка

  Фон

  `ManifestDesigner.Tab.Mouseover`

## <a name="tagging"></a>Добавление тегов
 Visual Studio поддерживает добавление тегов, что позволяет пользователю объявлять доступные для поиска ключевые слова в целях отслеживания. Например, руководители проектов и разработчики могут использовать Team Foundation Server (TFS) для добавления тегов к рабочим элементам. В приведенных ниже таблицах представлены имена цветов как для самого тега, так и для глифа (значка закрытия), который появляется при наведении указателя и в некоторых состояниях.

 ![Красная линия пометки тегами](../../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303 — 176_TaggingRedline")

 Используйте:
для пользовательского интерфейса, который поддерживает добавление тегов.

 Не используйте:
для любого другого пользовательского интерфейса.

### <a name="tag"></a>Тег
 Компонент

 Элемент

 Имя токена: Category.color

 ![Тег](../../extensibility/ux-guidelines/media/0303-177-tag.png "0303 — 177_Tag")

 **Default**

 Фон

 `Tag.Background`

 Передний план (текст)

 `Tag.Background`

 ![Тег при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 — 178_TagHover")

 **Наведение**

 Фон

 `Tag.HoverBackground`

 Передний план (текст)

 `Tag.HoverBackgroundText`

 ![Активный тег](../../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 — 179_TagPressed")

 **Pressed**

 Фон

 `Tag.PressedBackground`

 Передний план (текст)

 `Tag.PressedBackgroundText`

 ![Выбранный тег](../../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 — 180_TagSelected")

 **Selected**

 Фон

 `Tag.SelectedBackground`

 Передний план (текст)

 `Tag.SelectedBackgroundText`

### <a name="glyph-close-icon"></a>Глиф (значок закрытия)
 **Default**

 Компонент

 Элемент

 Имя токена: Category.color

 ![&#41;&#40;тега ](../../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 — 181_TagGlyph")

 **По умолчанию (тег по умолчанию)**

 Фон

 Н/Д

 Передний план (глиф)

 `Tag.TagHoverGlyph`

 **Наведение**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Тег &#40;&#41; глифа при наведении указателя](../../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 — 182_TagGlyphHover")

 **При наведении указателя (тег по умолчанию)**

 Фон

 `Tag.TagHoverGlyphHoverBackground`

 Передний план (глиф)

 `Tag.TagHoverGlyphHover`

 Рамка

 `Tag.TagHoverGlyphHoverBorder`

 **Pressed**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Тег &#40;глифа&#41; нажата](../../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 — 183_TagGlyphPressed")

 **Активен (тег по умолчанию)**

 Фон

 `Tag.TagHoverGlyphPressedBackground`

 Передний план (глиф)

 `Tag.TagHoverGlyphPressed`

 Рамка

 `Tag.TagHoverGlyphPressedBorder`

 **Тег выбран/глиф по умолчанию**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Выбранный тег](../../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 — 184_TagSelected")

 **По умолчанию (активный тег)**

 Фон

 Н/Д

 Передний план (глиф)

 `Tag.TagSelectedGlyph`

 **Тег выбран/глиф при наведении указателя**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Выбранный тег при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 — 185_TagSelectedHover")

 **При наведении указателя (тег выбран)**

 Фон

 `Tag.TagSelectedGlyphHoverBackground`

 Передний план (глиф)

 `Tag.TagSelectedGlyphHover`

 Рамка

 `Tag.TagSelectedGlyphHoverBorder`

 **Тег выбран/активный глиф**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Выбранный активный тег](../../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 — 186_TagSelectedPressed")

 **Активен (тег выбран)**

 Фон

 `Tag.TagSelectedGlyphPressedBackground`

 Передний план (глиф)

 `Tag.TagSelectedGlyphPressed`

 Рамка

 `Tag.TagSelectedGlyphPressedBorder`

## <a name="shell"></a>Оболочка

### <a name="background"></a>Фон

Фон среды состоит из двух слоев. Нижний слой представляет собой сплошной цвет, который охватывает всю интегрированную среду разработки. Верхний слой используется под командной полкой и между каналами автоматического скрытия окон инструментов по левому и правому краям интегрированной среды разработки. Начиная с версии Visual Studio 2013 верхний и нижний слои фона имеют одинаковый цвет при использовании светлой и темной тем.

![Красная линия фоновой оболочки](../../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303 — 187_ShellBackgroundRedline")

Используйте:
для областей, которые должны соответствовать фону среды Visual Studio.

Не используйте:
- в качестве заливки для областей, которые не являются фоновыми;

- в качестве фона, на котором должны размещаться элементы переднего плана.

  Компонент

  Элемент

  Имя токена: Category.color

  Нижний слой

  Фон

  `Environment.EnvironmentBackground`

  Компонент

  Элемент

  Имя токена: Category.color

  Верхний слой

  Фон

  *Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.*

  `Environment.EnvironmentBackgroundGradientBegin`

  `Environment.EnvironmentBackgroundGradientEnd`

  `Environment.EnvironmentBackgroundGradientMiddle1`

  `Environment.EnvironmentBackgroundGradientMiddle2`

### <a name="command-shelf"></a>Командная полка

Для фона командной полки используются два набора имен токенов: один для области размещения строки меню, а другой — для области размещения панелей команд. Отдельные группы на панели команд имеют собственные значения цветов фона, которые более подробно рассматриваются в разделе, посвященном панели команд. Цвета текста строки меню и панели команд рассматриваются в разделах, посвященных меню и панели команд.

![Красная линия командной полки](../../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303 — 188_CommandShelfRedline")

Используйте:
- для областей, где размещаются меню или панели инструментов;

- с правильным сочетанием имени фонового маркера/?.

Не используйте:
для областей, которые не похожи на командную полку.

  Компонент

  Элемент

  Имя токена: Category.color

  Строка меню

  Фон

  *Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.*

  `Environment.CommandShelfHighlightGradientBegin`

  `Environment.CommandShelfHighlightGradientMiddle`

  `Environment.CommandShelfHighlightGradientEnd`

  Панель команд

  Фон

  *Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.*

  `Environment.CommandShelfBackgroundGradientBegin`

  `Environment.CommandShelfBackgroundGradientMiddle`

  `Environment.CommandShelfBackgroundGradientEnd`

## <a name="toolbox"></a>Панель элементов
 Панель элементов — одно из стандартных окон инструментов, которое чаще всего используется в Visual Studio. По сути, это элемент управления типа "Дерево" с примененной к нему специальной темой и стилем.

 ![Красная линия панели инструментов](../../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303 — 189_ToolboxRedline")

 Используйте:
при разработке окна инструментов, которое всегда должно быть согласовано с панелью элементов оболочки.

 Не используйте:
для компонентов, которые не похожи на панель элементов, или если вы опасаетесь, что могут возникнуть проблемы с вашим пользовательским интерфейсом при изменении цветов панели элементов оболочки.

 **Default**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Родительский узел панели инструментов](../../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 — 190_ToolboxParentNode")

 **Родительский узел**

 ![Дочерний узел панели инструментов](../../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 — 191_ToolboxChildNode")

 **Дочерний узел**

 Фон

 `Environment.ToolboxContent`

 Заголовки

 `Environment.ToolWindowBackground`

 Отдельные элементы или все окно, если нет доступных элементов управления

 Рамка

 None

 Передний план (глиф)

 `Environment.ToolboxContent`

 Передний план (текст)

 `Environment.ToolboxContent`

 **Наведение**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Дочерний узел панели инструментов при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 — 192_ToolboxChildNodeHover")

 **Наведение указателя на дочерний узел панели элементов**

 Фон

 `Environment.ToolboxContentMouseOver`

 Только отдельные элементы

 Рамка

 None

 Передний план (текст)

 `Environment.ToolboxContentMouseOver`

 Только отдельные элементы

 **Selected**

 Компонент

 Элемент

 Имя токена: Category.color

 ![Родительский узел панели инструментов в фокусе](../../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 — 193_ToolboxParentNodeFocused")

 **Родительский узел с фокусом ввода**

 ![Дочерний узел панели инструментов в фокусе](../../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 — 194_ToolboxChildNodeFocused")

 **Дочерний узел с фокусом ввода**

 Фон

 `TreeView.SelectedItemActive`

 Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Рамка

 `TreeView.FocusVisualBorder`

 Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Передний план (глиф)

 `TreeView.SelectedItemActive`

 Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Передний план (текст)

 `TreeView.SelectedItemActive`

 Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 ![Родительский узел панели инструментов без фокуса ввода](../../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 — 195_ToolboxParentNodeUnfocused")

 **Родительский узел без фокуса ввода**

 ![Дочерний узел панели инструментов без фокуса ввода](../../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 — 196_ToolboxChildNodeUnfocused")

 **Дочерний узел без фокуса ввода**

 Фон

 `TreeView.SelectedItemInactive`

 Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Рамка

 None

 Передний план (глиф)

 `TreeView.SelectedItemInactive`

 Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Передний план (текст)

 `TreeView.SelectedItemInactive`

 Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)
