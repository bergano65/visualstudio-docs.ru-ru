---
title: Общие цвета для Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7b8b352b5abdeb975c09d3be95fc7384930eb022
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880933"
---
# <a name="shared-colors-for-visual-studio"></a>Общие цвета для Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [общие цвета для Visual Studio](https://docs.microsoft.com/visualstudio/extensibility/ux-guidelines/shared-colors-for-visual-studio).  
  
Если вы разрабатываете пользовательский интерфейс, в котором используются стандартные элементы оболочки Visual Studio, или вам нужно обеспечить согласованность элемента интерфейса с аналогичными функциями, используйте существующие имена токенов в файлах определения пакетов для выбора и назначения цветов. Таким образом можно обеспечить согласованность пользовательского интерфейса со всей средой Visual Studio и его автоматическое обновление при добавлении или обновлении тем.  
  
 В этом разделе описываются стандартные элементы пользовательского интерфейса и используемые ими имена токенов, на которые можно ссылаться при разработке похожего пользовательского интерфейса. Более подробные сведения о доступе к этим токенам цветов см. в разделе [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Используйте имена токенов правильно.  
  
-   **Используйте имена токенов в соответствии с функцией, а не самим цветом.** Стандартные общие цвета связаны с определенными элементами интерфейса и предназначены для использования только для аналогичных или похожих функций. Например, не используйте цвет выбранного поля со списком для анимированного индикатора хода выполнения только потому, что вам понравился цвет. Функции поля со списком и анимированного индикатора различны, и если цвет, связанный с полем со списком, изменится, он может оказаться неподходящим для анимированного элемента. Согласованное использование цветов помогает пользователям ориентироваться в интерфейсе и предотвращает путаницу.  
  
-   **Используйте цвета фона и текста в правильном сочетании.** Цвет фона, предназначенный для текста, имеет соответствующий цвет текста. Не используйте цвета текста, отличные от тех, которые определены для данного цвета фона. Если с цветом фона не связан цвет текста, не используйте его для поверхности, на которой будет выводиться текст. Другие сочетания цветов текста и фона могут сделать интерфейс неудобным для восприятия.  
  
-   **Используйте цвета элементов управления, соответствующие их расположению.** В определенных состояниях некоторые элементы управления Visual Studio не имеют отдельных цветов границ и фона. Эти цвета наследуются от областей, в которых они расположены. Всегда используйте имена токенов, которые подходят для того места, в котором вы размещаете элементы управления.  
  
> [!IMPORTANT]
>  Не используйте токены из категорий «Начальная страница» и «Cider».  
  
## <a name="command-structures"></a>Структура команд  
  
###  <a name="BKMK_CommandMenus"></a> Меню  
 Меню могут происходить в нескольких местах в Visual Studio: в строке главного меню, внедренные в документ или инструмент windows или правой кнопкой мыши таблицу, в разных местах внутри интегрированной среды разработки. Реализация меню, связанных с другими элементами пользовательского интерфейса, рассматривается в разделах, посвященных соответствующим элементам. Всегда используйте стандартную реализацию меню, предоставляемую средой Visual Studio. Однако в некоторых редких случаях доступ к стандартным меню Visual Studio может отсутствовать. В таких ситуациях используйте указанные ниже имена токенов для обеспечения согласованности пользовательского интерфейса с другими меню в Visual Studio.  
  
 ![Красная линия меню](../../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303 000_MenuRedline")  
  
 Используйте:  
 -   если нужно создать пользовательское меню;  
  
-   если есть новый компонент пользовательского интерфейса, который должен соответствовать меню Visual Studio.  
  
 Не используйте:  
 цвет фона сам по себе. Всегда используйте определенное сочетание цвета фона и цвета переднего плана.  
  
#### <a name="menu-title"></a>Заголовок меню  
 Заголовок меню состоит из фона, границы и текста заголовка, а также необязательного глифа (обычно если меню находится на панели команд).  
  
 ![Красная линия заголовка меню](../../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303 001_MenuTitleRedline")  
  
 Используйте:  
 при создании пользовательского заголовка меню.  
  
 Не используйте:  
 -   для каких-либо элементов, которые не должны всегда соответствовать заголовку меню;  
  
-   в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Заголовок меню по умолчанию](../../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 002_MenuTitleDefault")  
  
 **Заголовок меню**  
  
 Фон  
  
 Нет  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextActive`  
  
 ![Заголовок меню с глифом по умолчанию](../../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")  
  
 **Заголовок меню с глифом**  
  
 Передний план (глиф)  
  
 `Environment.CommandBarMenuGlyph`  
  
 Border  
  
 Нет  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Заголовок меню при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 004_MenuTitleHover")  
  
 **Заголовок меню**  
  
 Фон  
  
 `Environment.CommandBarMouseOverBackgroundBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextHover`  
  
 ![Заголовок меню с глифом при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")  
  
 **Заголовок меню с глифом**  
  
 Передний план (глиф)  
  
 `Environment.CommandBarMenuMouseOverGlyph`  
  
 Border  
  
 `Environment.CommandBarBorder`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Активная кнопка заголовка меню](../../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 006_MenuTitlePressed")  
  
 **Заголовок меню**  
  
 Фон  
  
 `Environment.CommandBarMenuBackgroundGradientBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextActive`  
  
 ![Заголовок меню с глифом при нажатии](../../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")  
  
 **Заголовок меню с глифом**  
  
 Передний план (глиф)  
  
 `Environment.CommandBarMenuMouseDownGlyph`  
  
 Border  
  
 `Environment.CommandBarMenuBorder`  
  
 Только с левой, верхней и правой сторон.  
  
 **Отключено**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Заголовок меню с глифом отключена](../../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")  
  
 **Заголовок меню с глифом**  
  
 Фон  
  
 Нет  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextInactive`  
  
 Передний план (глиф)  
  
 `Environment.CommandBarTextInactive`  
  
 Border  
  
 Нет  
  
#### <a name="menu"></a>Меню  
 Отдельный пункт меню состоит из текста и необязательных значка, флажка или глифа подменю. Его цвета фона и текста меняются при наведении указателя. Этот токен цвета представляет собой пару, состоящую из цвета фона и цвета переднего плана.  
  
 ![Красная линия пунктов меню](../../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303 009_MenuItemRedline")  
  
 Используйте:  
 для любого раскрывающегося списка, открывающегося из строки меню или панели команд.  
  
 Не используйте:  
 -   для любого раскрывающегося списка, открывающегося в другом контексте;  
  
-   в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Меню по умолчанию](../../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")  
  
 **Menu**  
  
 Фон  
  
 `Environment.CommandBarMenuBackgroundGradientBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextActive`  
  
 Передний план (глиф подменю)  
  
 `Environment.CommandBarMenuSubmenuGlyph`  
  
 Border  
  
 `Environment.CommandBarMenuBorder`  
  
 Фон канала значка  
  
 `Environment.CommandBarMenuIconBackground`  
  
 Separator  
  
 `Environment.CommandBarMenuSeparator`  
  
 Тень  
  
 `Environment.DropShadowBackground`  
  
 ![Меню с установленным флажком](../../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 011_MenuChecked")  
  
 **Помечено**  
  
 Флажок  
  
 `Environment.CommandBarCheckBox`  
  
 Фон флажка  
  
 `Environment.CommandBarSelectedIcon`  
  
 ![Выбранное меню](../../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 012_MenuSelected")  
  
 **Выбранные**  
  
 Фон значка  
  
 `Environment.CommandBarSelected`  
  
 Граница значка  
  
 `Environment.CommandBarSelectedBorder`  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Меню при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 013_MenuHover")  
  
 **Пункт меню**  
  
 Фон  
  
 `Environment.CommandBarMenuItemMouseOver`  
  
 Передний план (текст)  
  
 `Environment.CommandBarMenuItemMouseOver`  
  
 Передний план (глиф подменю)  
  
 `Environment.CommandBarMenuMouseOverSubmenuGlyph`  
  
 ![Меню при наведении указателя мыши проверяется](../../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 014_MenuHoverChecked")  
  
 **Помечено**  
  
 Флажок  
  
 `Environment.CommandBarCheckBoxMouseOver`  
  
 Фон флажка  
  
 `Environment.CommandBarHoverOverSelectedIcon`  
  
 ![Меню при наведении указателя мыши выбранных](../../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 015_MenuHoverSelected")  
  
 **Выбранные**  
  
 Фон значка  
  
 `Environment.CommandBarHoverOverSelected`  
  
 Граница значка  
  
 `Environment.CommandBarHoverOverSelectedIconBorder`  
  
 **Отключено**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Неактивное меню](../../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 016_MenuDisabled")  
  
 Элемент меню  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextInactive`  
  
 Передний план (глиф подменю)  
  
 `Environment.CommandBarMenuSubmenuGlyph`  
  
 ![Неактивное меню проверяется](../../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 017_MenuDisabledChecked")  
  
 Помечено  
  
 Флажок  
  
 `Environment.CommandBarCheckBoxDisabled`  
  
 Фон флажка  
  
 `Environment.CommandBarSelectedIconDisabled`  
  
### <a name="command-bar"></a>Панель команд  
 Панель команд может встречаться в интегрированной среде разработки Visual Studio в нескольких местах. В первую очередь это командная полка и окна инструментов и документов.  
  
 Как правило, следует всегда использовать стандартную реализацию панели команд, предоставляемую средой Visual Studio. Использование стандартного механизма обеспечивает правильное отображение визуальных элементов и согласованное поведение интерактивных элементов и других элементов управления панели команд Visual Studio. Однако если вам необходимо создать собственную панель команд, следует правильно оформить ее с помощью указанных ниже имен токенов.  
  
 ![Красная линия панели команд](../../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303 018_CommandBarRedline")  
  
 ![Красная линия кнопки переполнения](../../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303 019_OverflowButtonRedline")  
  
 Используйте:  
 в местах, где требуется внедренная панель команд, но нельзя использовать стандартную реализацию панели команд Visual Studio.  
  
 Не используйте:  
 -   для элементов пользовательского интерфейса, которые не похожи на панель команд;  
  
-   для компонентов панели команд, отличных от тех, для которых определены имена токенов.  
  
#### <a name="command-bar-group"></a>Группа панели команд  
 Группа панели команд состоит из связанного набора элементов управления панели команд и может содержать любое количество кнопок, разворачивающихся кнопок, раскрывающихся меню, полей со списками или меню. Цвета этих элементов управления определяются отдельными именами токенов, которые рассматриваются в других частях этого руководства. Разделительная линия служит для разделения группы на панели команд в связанные подгруппы.  
  
 ![Красная линия группа панели команд](../../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303 020_CommandBarGroupRedline")  
  
 Используйте:  
 в местах, где требуется внедренная панель команд, но нельзя использовать стандартную реализацию панели команд Visual Studio.  
  
 Не используйте:  
 -   для элементов пользовательского интерфейса, которые не похожи на панель команд;  
  
-   для компонентов панели команд, отличных от тех, для которых определены имена токенов.  
  
 **По умолчанию** (нет других состояний)  
  
 Элемент  
  
 Имя токена: Category.color  
  
 Фон  
  
 `Environment.CommandBarGradientBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Border  
  
 `Environment.CommandBarToolBarBorder`  
  
 Маркер перетаскивания  
  
 `Environment.CommandBarDragHandle`  
  
 Separator  
  
 `Environment.CommandBarToolBarSeparator`  
  
 `Environment.CommandBarToolBarSeparatorHighlight`  
  
#### <a name="command-icons"></a>Значки команд  
 ![Красная линия значка команды](../../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303 021_CommandIconRedline1")  
  
 ![Красная линия значка команды](../../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303 022_CommandIconRedline2")  
  
 Используйте:  
 для кнопок, которые будут размещаться на панели команд.  
  
 Не используйте:  
 -   для элементов управления, которые имеют собственные имена токенов;  
  
-   в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Команда значок по умолчанию](../../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 023_CommandIconDefault")  
  
 **Default**  
  
 Фон  
  
 Н/Д (наследуется от фона панели команд)  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextActive`  
  
 Border  
  
 Н/Д  
  
 ![Команда значок по умолчанию выбран](../../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")  
  
 **Выбранные**  
  
 Фон  
  
 `Environment.CommandBarSelected`  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextSelected`  
  
 Border  
  
 `Environment.CommandBarSelectedBorder`  
  
 **При наведении указателя мыши и клавиатуры с фокусом ввода**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Значок команды при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 025_CommandIconHover")  
  
 **Стандартный при наведении курсора мыши**  
  
 Фон  
  
 `Environment.CommandBarMouseOverBackgroundBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextHover`  
  
 Border  
  
 `Environment.CommandBarBorder`  
  
 ![Команды при наведении значок выбранного](../../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 026_CommandIconHoverSelected")  
  
 **Выбран при наведении курсора мыши**  
  
 Фон  
  
 `Environment.CommandBarHoverOverSelected`  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextHoverOverSelected`  
  
 Border  
  
 `Environment.CommandBarHoverOverSelectedIconBorder`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Активный значок команды](../../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 027_CommandIconPressed")  
  
 **Активный значок команды**  
  
 Фон  
  
 `Environment.CommandBarMouseDownBackgroundBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextMouseDown`  
  
 Border  
  
 `Environment.CommandBarBorder`  
  
 **Отключено**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Неактивный значок команды](../../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 028_CommandIconDisabled")  
  
 **Неактивный значок команды**  
  
 Фон  
  
 Н/Д (наследуется от фона панели команд)  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextInactive`  
  
 Border  
  
 Н/Д  
  
####  <a name="BKMK_CommandComboBox"></a> Поле со списком  
  
> [!IMPORTANT]
>  Поле со списком похоже на раскрывающийся список, но включает область для ввода и редактирования текста. Если раскрывающийся список не включает область для ввода и редактирования текста, используйте токены цветов, указанные в разделе [Drop-down](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).  
  
 ![Красная линия со списком](../../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303 029_ComboBoxRedline")  
  
 Используйте:  
 -   при создании пользовательских полей со списками;  
  
-   при создании элемента управления панели команд, похожего на поле со списком.  
  
 Не используйте:  
 -   для каких-либо элементов, которые не должны всегда соответствовать пользовательскому интерфейсу панели команд;  
  
-   если есть доступ к оформленному полю со списком.  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Поле ввода поля со списком](../../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 030_ComboBoxInputField")  
  
 **Поле ввода**  
  
 Фон  
  
 `Environment.ComboBoxBackground`  
  
 Передний план (текст)  
  
 `Environment.ComboBoxText`  
  
 Border  
  
 `Environment.ComboBoxBorder`  
  
 Separator  
  
 Без разделителя  
  
 ![Раскрывающееся поле со списком&#45;нажатой кнопку](../../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")  
  
 **Кнопка раскрывающегося списка**  
  
 Фон  
  
 Н/Д (наследуется)  
  
 Передний план (глиф)  
  
 `Environment.ComboBoxGlyph`  
  
 ![Поле со списком&#47;drop&#45;списку](../../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")  
  
 **Выберите в раскрывающемся списке**  
  
 Фон  
  
 `Environment.ComboBoxPopupBackgroundBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.ComboBoxItemText`  
  
 Border  
  
 `Environment.ComboBoxPopupBorder`  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Поле ввода поля со списком при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")  
  
 **Поле ввода**  
  
 Фон  
  
 `Environment.ComboBoxMouseOverBackgroundBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.ComboBoxMouseOverText`  
  
 Border  
  
 `Environment.ComboBoxMouseOverBorder`  
  
 Separator  
  
 `Environment.ComboBoxMouseOverSeparator`  
  
 ![Поле со списком&#47;drop&#45;кнопка при наведении указателя мыши вниз](../../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")  
  
 **Кнопка раскрывающегося списка**  
  
 Фон  
  
 `Environment.ComboBoxButtonMouseOverBackground`  
  
 Передний план (глиф)  
  
 `Environment.ComboBoxMouseOverGlyph`  
  
 ![Поле со списком&#47;drop&#45;вниз списка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")  
  
 **Выберите в раскрывающемся списке**  
  
 Фон (пункт меню)  
  
 `Environment.ComboBoxItemMouseOverBackground`  
  
 Передний план (текст)  
  
 `Environment.ComboBoxItemMouseOverText`  
  
 Граница (пункт меню)  
  
 `Environment.ComboBoxItemMouseOverBorder`  
  
 **С фокусом ввода**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Цвет.категория  
  
 ![Поле ввода поля со списком с фокусом ввода](../../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")  
  
 **Поле ввода**  
  
 Фон  
  
 `Environment.ComboBoxFocusedBackground`  
  
 Передний план (текст)  
  
 `Environment.ComboBoxFocusedText`  
  
 Border  
  
 `Environment.ComboBoxFocusedBorder`  
  
 Separator  
  
 `Environment.ComboBoxFocusedButtonSeparator`  
  
 ![Поле со списком&#47;drop&#45;кнопка с фокусом ввода вниз](../../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")  
  
 **Кнопка раскрывающегося списка**  
  
 Фон  
  
 `Environment.ComboBoxFocusedButtonBackground`  
  
 Передний план (глиф)  
  
 `Environment.ComboBoxFocusedGlyph`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Цвет.категория  
  
 ![Поле со списком активное поле ввода поля](../../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")  
  
 **Поле ввода**  
  
 Фон  
  
 `Environment.ComboBoxMouseDownBackground`  
  
 Передний план (текст)  
  
 `Environment.ComboBoxMouseDownText`  
  
 Border  
  
 `Environment.ComboBoxMouseDownBorder`  
  
 Separator  
  
 `Environment.ComboBoxMouseDownSeparator`  
  
 ![Поле со списком&#47;drop&#45;вниз была нажата кнопка](../../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")  
  
 **Кнопка раскрывающегося списка**  
  
 Фон  
  
 `Environment.ComboBoxButtonMouseDownBackground`  
  
 Передний план (глиф)  
  
 `Environment.ComboBoxMouseDownGlyph`  
  
 **Отключено**  
  
 ![Поле со списком неактивное поле ввода](../../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")  
  
 **Поле ввода**  
  
 Фон  
  
 `Environment.ComboBoxDisabledBackground`  
  
 Передний план (текст)  
  
 `Environment.ComboBoxDisabledText`  
  
 Border  
  
 `Environment.ComboBoxDisabledBorder`  
  
 Separator  
  
 Без разделителя  
  
 ![Поле со списком&#47;drop&#45;вниз неактивная кнопка](../../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")  
  
 **Кнопка раскрывающегося списка**  
  
 Фон  
  
 Нет  
  
 Передний план (глиф)  
  
 `Environment.ComboBoxDisabledGlyph`  
  
####  <a name="BKMK_CommandDropDown"></a> Раскрывающегося списка  
  
> [!IMPORTANT]
>  Раскрывающийся список похож на поле со списком, но не имеет области для ввода и редактирования текста. Если раскрывающийся список включает область для ввода и редактирования текста, используйте токены цветов, указанные в разделе [Combo box](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).  
  
 ![DROP&#45;вниз красная линия](../../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303 042_DropdownRedline")  
  
 Используйте:  
 при создании пользовательских элементов управления типа "раскрывающийся список".  
  
 Не используйте:  
 -   для каких-либо элементов, отличных от раскрывающегося списка;  
  
-   для полей со списками или разворачивающихся кнопок.  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![DROP&#45;вниз поле выбора](../../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 043_DropdownSelectionField")  
  
 **Поле выбора**  
  
 Фон  
  
 `Environment.DropDownBackground`  
  
 Передний план (текст)  
  
 `DropDownText`  
  
 Border  
  
 `DropDownBorder`  
  
 Separator  
  
 Без разделителя  
  
 ![DROP&#45;нажатой кнопку](../../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 044_DropdownButton")  
  
 **Кнопка раскрывающегося списка**  
  
 Фон  
  
 Нет  
  
 Передний план (глиф)  
  
 `Environment.DropDownGlyph`  
  
 ![DROP&#45;списку](../../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 045_DropdownList")  
  
 **Выберите в раскрывающемся списке**  
  
 Фон  
  
 `Environment.DropDownPopupBackgroundBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.ComboBoxItemText`  
  
 Border  
  
 `Environment.DropDownPopupBorder`  
  
 Тень  
  
 `Environment.DropShadowBackground`  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![DROP&#45;вниз поле выбора при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")  
  
 **Поле выбора**  
  
 Фон  
  
 `Environment.DropDownMouseOverBackgroundBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.DropDownMouseOverText`  
  
 Border  
  
 `Environment.DropDownMouseOverBorder`  
  
 Separator  
  
 `Environment.DropDownButtonMouseOverSeparator`  
  
 ![DROP&#45;кнопка при наведении указателя мыши вниз](../../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 047_DropdownButtonHover")  
  
 **Кнопка раскрывающегося списка**  
  
 Фон  
  
 `Environment.DropDownButtonMouseOverBackground`  
  
 Передний план (глиф)  
  
 `Environment.DropDownMouseOverGlyph`  
  
 ![DROP&#45;вниз списка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 048_DropdownListHover")  
  
 **Выберите в раскрывающемся списке**  
  
 Фон (пункт меню)  
  
 `Environment.ComboBoxItemMouseOverBackground`  
  
 Передний план (текст)  
  
 `Environment.ComboBoxItemMouseOverText`  
  
 Граница (пункт меню)  
  
 `Environment.ComboBoxItemMouseOverBorder`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![DROP&#45;вниз поле выбора нажата](../../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")  
  
 **Поле выбора**  
  
 Фон  
  
 `Environment.DropDownMouseDownBackground`  
  
 Передний план (текст)  
  
 `Environment.DropDownMouseDownText`  
  
 Border  
  
 `Environment.DropDownMouseDownBorder`  
  
 Separator  
  
 `Environment.DropDownButtonMouseDownSeparator`  
  
 ![DROP&#45;вниз была нажата кнопка](../../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")  
  
 **Кнопка раскрывающегося списка**  
  
 Фон  
  
 `Environment.DropDownButtonMouseDownBackground`  
  
 Передний план (глиф)  
  
 `Environment.DropDownMouseDownGlyph`  
  
 **Отключено**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![DROP&#45;вниз неактивное поле выбора](../../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")  
  
 Фон  
  
 `Environment.DropDownDisabledBackground`  
  
 Передний план (текст)  
  
 `Environment.DropDownDisabledText`  
  
 Border  
  
 `Environment.DropDownDisabledBorder`  
  
 Separator  
  
 Без разделителя  
  
 ![DROP&#45;вниз неактивная кнопка](../../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")  
  
 Фон  
  
 Н/Д  
  
 Передний план (глиф)  
  
 `Environment.DropDownDisabledGlyph`  
  
#### <a name="split-button"></a>Разворачивающаяся кнопка  
 Для разворачивающихся кнопок используются многие имена токенов, определенные для других элементов управления панели команд, таких как кнопки, меню и текст панели команд. Все необходимые имена токенов для действий и кнопок раскрывающихся списков приводятся здесь еще раз для удобства. Раскрывающиеся списки разворачивающихся кнопок являются реализацией [Menus](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)панели команд.  
  
 ![Красная линия разворачивающейся кнопки](../../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303 053_SplitButtonRedline")  
  
 Используйте:  
 при создании пользовательской разворачивающейся кнопки.  
  
 Не используйте:  
 -   для других видов кнопок;  
  
-   в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Разворачивающаяся кнопка](../../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")  
  
 **Разворачивающаяся кнопка (по умолчанию)**  
  
 Фон  
  
 Нет  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextActive`  
  
 Передний план (глиф)  
  
 `Environment.CommandBarSplitButtonGlyph`  
  
 Border  
  
 Н/Д  
  
 Separator  
  
 Н/Д  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Разворачивающаяся кнопка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")  
  
 **Разворачивающаяся кнопка (при наведении курсора мыши)**  
  
 Фон  
  
 `Environment.CommandBarMouseOverBackgroundBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextHover`  
  
 Передний план (глиф)  
  
 `Environment.CommandBarSplitButtonMouseOverGlyph`  
  
 Border  
  
 `Environment.CommandBarBorder`  
  
 Separator  
  
 `Environment.CommandBarSplitButtonSeparator`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Активная Разворачивающаяся кнопка](../../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")  
  
 **Разворачивающаяся кнопка (активная)**  
  
 Фон  
  
 `Environment.CommandBarMouseDownBackgroundBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextMouseDown`  
  
 Передний план (глиф)  
  
 `Environment.CommandBarSplitButtonMouseDownGlyph`  
  
 Border  
  
 `Environment.CommandBarBorder`  
  
 Separator  
  
 Н/Д  
  
 **Отключено**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Неактивная Разворачивающаяся кнопка](../../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")  
  
 **Разворачивающаяся кнопка (неактивная)**  
  
 Фон  
  
 Н/Д  
  
 Передний план (текст)  
  
 `Environment.ComboBoxItemTextInactive`  
  
 Передний план (глиф)  
  
 `Environment.CommandBarTextInactive`  
  
 Border  
  
 Н/Д  
  
 Separator  
  
 Н/Д  
  
#### <a name="more-options-and-overflow-buttons"></a>Кнопки "Дополнительно" и "Переполнение"  
 Кнопка "Дополнительно" используется, если группа панели команд может настраиваться путем добавления или удаления связанных кнопок. Кнопка "Переполнение" появляется, если панель команд усекается из-за отсутствия места по горизонтали. При ее нажатии открывается меню, содержащее кнопки, которые не поместились на панели команд. Цвета этих двух кнопок определяются одним и тем же набором имен токенов.  
  
 ![Красная линия дополнительных параметров](../../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303 058_MoreOptionsRedline")  
  
 Используйте:  
 для пользовательских кнопок "Дополнительно" и "Переполнение".  
  
 Не используйте:  
 для кнопок, которые по своему предназначению отличаются от кнопки "Дополнительно" или "Переполнение".  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Дополнительные параметры](../../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 059_MoreOptions")  
  
 **Дополнительные параметры**  
  
 ![Кнопка переполнения](../../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 060_Overflow")  
  
 **переполнение**  
  
 Фон  
  
 `Environment.CommandBarOptionsBackground`  
  
 Передний план (глиф)  
  
 `Environment.CommandBarOptionsGlyph`  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Дополнительные параметры при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 061_MoreOptionsHover")  
  
 **Дополнительные параметры**  
  
 ![Переполнение при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 062_OverflowOptions")  
  
 **переполнение**  
  
 Фон  
  
 `Environment.CommandBarOptionsMouseOverBackgroundBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (глиф)  
  
 `Environment.CommandBarOptionsMouseDownGlyph`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Дополнительные параметры нажата](../../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 063_MoreOptionsPressed")  
  
 **Дополнительные параметры**  
  
 ![Переполнение при нажатии](../../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 064_OverflowPressed")  
  
 **переполнение**  
  
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
  
 ![Красная линия окна закрепленного документа](../../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")  
  
 **Закрепленное окно документа**  
  
 ![Красная линия окна плавающего документа](../../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")  
  
 **Плавающее окно**  
  
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
  
 Border  
  
 `Environment.ToolWindowBorder`  
  
 ![Кадр с фокусом ввода](../../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")  
  
 **Рамка: перемещаемая, с фокусом ввода**  
  
 Фон  
  
 `Environment.ToolWindowFloatingFrame`  
  
 Передний план (текст)  
  
 `Environment.ToolWindowFloatingFrame`  
  
 Передний план (глиф)  
  
 `Environment.RaftedWindowButtonActiveGlyph`  
  
 Border  
  
 `Environment.MainWindowActiveDefaultBorder`  
  
 Граница (глиф)  
  
 `Environment.RaftedWindowButtonActiveBorder`  
  
 Задается как прозрачная  
  
 ![Кадр без фокуса ввода](../../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")  
  
 **Рамка: перемещаемая, без фокуса ввода**  
  
 Фон  
  
 `Environment.ToolWindowFloatingFrameInactive`  
  
 Передний план (текст)  
  
 `Environment.ToolWindowFloatingFrameInactive`  
  
 Передний план (глиф)  
  
 `Environment.RaftedWindowButtonInactiveGlyph`  
  
 Border  
  
 `Environment.MainWindowInactiveBorder`  
  
 Граница (глиф)  
  
 `Environment.RaftedWindowButtonInactiveBorder`  
  
 Задается как прозрачная  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Кадр с фокусом ввода при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 069_FrameFocusedHover")  
  
 **Рамка: перемещаемая, с фокусом ввода**  
  
 Фон (глиф)  
  
 `Environment.RaftedWindowButtonHoverActive`  
  
 Передний план (глиф)  
  
 `Environment.RaftedWindowButtonHoverActiveGlyph`  
  
 Граница (глиф)  
  
 `Environment.RaftedWindowButtonHoverActiveBorder`  
  
 ![Кадр без фокуса ввода при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 070_FrameUnfocusedHover")  
  
 **Рамка: перемещаемая, без фокуса ввода**  
  
 Фон (глиф)  
  
 `EnvironmentRaftedWindowButtonHoverInactive`  
  
 Передний план (глиф)  
  
 `Environment.RaftedWindowButtonHoverInactiveGlyph`  
  
 Граница (глиф)  
  
 `Environment.RaftedWindowButtonHoverInactiveBorder`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Кадр с фокусом ввода нажатом](../../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 071_FrameFocusedPressed")  
  
 **Рамка: перемещаемая, с фокусом ввода**  
  
 Фон (глиф)  
  
 `Environment.RaftedWindowButtonDown`  
  
 Передний план (глиф)  
  
 `Environment.RaftedWindowButtonDownGlyph`  
  
 Граница (глиф)  
  
 `Environment.RaftedWindowButtonDownBorder`  
  
### <a name="document-tabs"></a>Вкладки документов  
 Вкладки документов размещаются в канале вкладок и указывают, какие документы в настоящее время открыты, а также какой документ в настоящий момент выбран или активен. Окна инструментов также могут закрепляться в канале вкладок документов, если пользователь размещает их там. В этом случае для них используются те же цвета, что и для окон документов. Если вы создаете пользовательский интерфейс, цвета которого должны всегда соответствовать цветам окна документа (в том числе при обновлении темы или установке новых тем), то используйте ссылки на указанные ниже токены цветов.  
  
 ![Красная линия вкладки документов](../../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303 072_DocumentTabRedline")  
  
 Используйте:  
 при создании пользовательского интерфейса, который должен соответствовать вкладкам документов и автоматически изменяться при обновлении тем или добавлении новых цветов темы.  
  
 Не используйте:  
 для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
#### <a name="open-document-tabs"></a>Вкладки открытых документов  
 Каждый открытый документ имеет вкладку в канале вкладок документов, на которой показано его имя. Документы могут быть либо выбраны, либо открыты в фоновом режиме. На их вкладках указываются перечисленные ниже состояния.  
  
-   Выбранная вкладка представляет документ, который в настоящее время отображается в контейнере документа. Выбранная вкладка имеет границу документа, которая располагается по верхнему краю контейнера документа.  
  
-   Фоновые вкладки — это все вкладки документов, кроме выбранной в настоящий момент вкладки. При щелчке по такой вкладке она становится выбранной и получает цвета фона, границы и текста с соответствующими именами токенов.  
  
 ![Красная линия открытой вкладки документов](../../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")  
  
 Используйте:  
 при создании пользовательских вкладок документов.  
  
 Не используйте:  
 -   для временных вкладок (вкладок предварительного просмотра);  
  
-   для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
#### <a name="selected-tab"></a>Выбранная вкладка  
 **С фокусом ввода**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Выбранная вкладка с фокусом ввода](../../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 074_SelectedTabFocused")  
  
 **Выбранная вкладка документа, с фокусом ввода**  
  
 Фон  
  
 `Environment.FileTabSelectedGradientTop`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.FileTabSelectedText`  
  
 Border  
  
 `Environment.FileTabSelectedBorder`  
  
 Цвет совпадает с цветом фона.  
  
 Граница документа  
  
 `Environment.FileTabDocumentBorderBackground`  
  
 **Без фокуса ввода**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Выбранная вкладка без фокуса ввода](../../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 075_SelectedTabUnfocused")  
  
 **Выбранная вкладка документа, без фокуса ввода**  
  
 Фон  
  
 `Environment.FileTabInactiveGradientTop`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.FileTabInactiveText`  
  
 Border  
  
 `Environment.FileTabInactiveBorder`  
  
 Цвет совпадает с цветом фона.  
  
 Граница документа  
  
 `Environment.FileTabInactiveDocumentBorderBackground`  
  
#### <a name="background-tab"></a>Вкладка фона  
 **Default**  
  
 ![Вкладка фона](../../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 076_BackgroundTab")  
  
 **Вкладка фона по умолчанию**  
  
 Фон  
  
 `Environment.FileTabBackground`  
  
 Передний план (текст)  
  
 `Environment.FileTabText`  
  
 Border  
  
 `Environment.FileTabBorder`  
  
 Цвет совпадает с цветом фона.  
  
 **При наведении курсора мыши**  
  
 ![Вкладка фона при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 077_BackgroundTabHover")  
  
 **Вкладка фона при наведении курсора мыши**  
  
 Фон  
  
 `Environment.FileTabHotGradientTop`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.FileTabHotText`  
  
 Border  
  
 `Environment.FileTabHotBorder`  
  
 Цвет совпадает с цветом фона.  
  
#### <a name="preview-tab"></a>Вкладка предварительного просмотра  
 Вкладка предварительного просмотра отображается в правой части канала вкладок документов, когда пользователь щелкает элемент в окне инструментов обозревателя решений. Она служит для предварительного просмотра документа и дает пользователю возможность сохранять документ открытым в левой части канала вкладок документов. Одновременно может быть открыта только одна вкладка предварительного просмотра. Так же как открытые вкладки, вкладки предварительного просмотра имеют как фоновое, так и выбранное состояния и в активном состоянии могут получать фокус ввода и терять его.  
  
 ![Красная линия вкладки предварительного просмотра](../../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303 078_PreviewTabRedline")  
  
 Используйте:  
 при создании временной области предварительного просмотра, если какой-либо элемент должен иметь цвет текущей вкладки предварительного просмотра.  
  
 Не используйте:  
 -   для любого документа или вкладки, которая не является временной (не служит для предварительного просмотра);  
  
-   для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
 **Выбранная вкладка предварительного просмотра: с фокусом ввода**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Вкладка предварительного просмотра с фокусом ввода](../../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 079_PreviewTabFocused")  
  
 **Вкладка предварительного просмотра фокусом ввода**  
  
 Фон  
  
 `Environment.FileTabProvisionalSelectedActive`  
  
 Передний план (текст)  
  
 `Environment.FileTabProvisionalSelectedActiveForeground`  
  
 Border  
  
 `Environment.FileTabProvisionalSelectedActiveBorder`  
  
 Цвет совпадает с цветом фона.  
  
 Граница документа  
  
 `Environment.FileTabProvisionalSelectedActiveBorder`  
  
 **Выбранная вкладка предварительного просмотра: без фокуса ввода**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Вкладка предварительного просмотра без фокуса ввода](../../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 080_PreviewTabUnfocused")  
  
 **Вкладка предварительного просмотра без фокуса ввода**  
  
 Фон  
  
 `Environment.FileTabProvisionalSelectedInactive`  
  
 Передний план (текст)  
  
 `Environment.FileTabProvisionalSelectedInactiveForeground`  
  
 Border  
  
 `Environment.FileTabProvisionalSelectedInactiveBorder`  
  
 Граница документа  
  
 `Environment.FileTabProvisionalSelectedInactiveBorder`  
  
 **Фоновая вкладка предварительного просмотра: по умолчанию**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Вкладка фона предварительного просмотра](../../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 081_PreviewBackgroundTab")  
  
 **Фоновая вкладка предварительного просмотра**  
  
 Фон  
  
 `Environment.FileTabProvisionalInactive`  
  
 Передний план (текст)  
  
 `Environment.FileTabProvisionalInactiveForeground`  
  
 Border  
  
 `Environment.FileTabProvisionalInactiveBorder`  
  
 Цвет совпадает с цветом фона.  
  
 **Фоновая вкладка предварительного просмотра: при наведении указателя мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Вкладка фона предварительного просмотра при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")  
  
 **Фоновая вкладка предварительного просмотра при наведении курсора мыши**  
  
 Фон  
  
 `Environment.FileTabProvisionalHover`  
  
 Передний план (текст)  
  
 `Environment.FileTabProvisionalHoverForeground`  
  
 Border  
  
 `Environment.FileTabProvisionalHoverBorder`  
  
 Цвет совпадает с цветом фона.  
  
#### <a name="document-overflow-button"></a>Кнопка переполнения документа  
 Кнопка переполнения документа присутствует, если открыт один или несколько документов, вне зависимости от того, имеется ли в текущей конфигурации пространство по вертикали для размещения всех вкладок документов. В раскрывающемся меню переполнения документа, к которому применяются цвета **CommandBarMenu** (см. раздел [Menus](../../misc/shared-colors.md#BKMK_CommandMenus)), приводится список всех открытых документов, как видимых, так и скрытых. Глиф переполнения меняется в зависимости от того, отображаются ли все открытые документы в канале вкладок.  
  
 ![Красная линия переполнения](../../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303 083_OverflowRedline")  
  
 Используйте:  
 при создании пользовательской кнопки переполнения документа.  
  
 Не используйте:  
 -   для пользовательского интерфейса, отличного от кнопки переполнения;  
  
-   для кнопок переполнения панели команд.  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Overflow](../../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 084_Overflow")  
  
 **Кнопка переполнения документа**  
  
 Фон  
  
 `Environment.DocWellOverflowButtonBackground`  
  
 Передний план (глиф)  
  
 `Environment.DocWellOverflowButtonGlyph`  
  
 Border  
  
 Н/Д  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Переполнение при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 085_OverflowHover")  
  
 **Кнопка переполнения документа при наведении курсора мыши**  
  
 Фон  
  
 `Environment.DocWellOverflowButtonMouseOverBackground`  
  
 Передний план (глиф)  
  
 `Environment.DocWellOverflowButtonMouseOverGlyph`  
  
 Border  
  
 `Environment.DocWellOverflowButtonMouseOverBorder`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Переполнение при нажатии](../../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 086_OverflowPressed")  
  
 **Активная кнопка переполнения документа**  
  
 Фон  
  
 `Environment.DocWellOverflowButtonMouseDownBackground`  
  
 Передний план (глиф)  
  
 `Environment.DocWellOverflowButtonMouseDownGlyph`  
  
 Border  
  
 `Environment.DocWellOverflowButtonMouseDownBorder`  
  
## <a name="tool-windows"></a>Окна инструментов  
 Воссоздавать окна инструментов не нужно, так как они предоставляются средой Visual Studio. Однако может потребоваться использовать цвета, применяемые в окнах инструментов, чтобы ваш пользовательский интерфейс был согласован с этой частью среды Visual Studio.  
  
 ![Красная линия окна инструментов](../../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303 087_ToolWindowRedline")  
  
 Используйте:  
 при создании пользовательского интерфейса, соответствующего окнам инструментов.  
  
 Не используйте:  
 для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
### <a name="tool-window-frame"></a>Рамка окна инструментов  
 Окна инструментов в Visual Studio используются для множества различных задач и могут иметь одно из нескольких состояний. Если окно инструментов открыто, оно может быть назначено одной из четырех сторон области документа. Окна инструментов также могут перемещаться за пределы интегрированной среды документов, что позволяет размещать их в любом месте экрана. Перемещаемые окна всегда находятся поверх интегрированной среды разработки. Наконец, окна инструментов могут закрепляться как окна документов и отображаться в виде вкладок в контейнере документа. К окнам инструментов, закрепленным как окна документов, частично применяются имена токенов окна документа.  
  
 ![Красная линия фрейм окна инструментов](../../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")  
  
 Используйте:  
 при создании пользовательского интерфейса, соответствующего окнам инструментов.  
  
 Не используйте:  
 для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
 **Закреплено**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Окно инструментов закреплено](../../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 089_ToolWindowDocked")  
  
 Фон  
  
 `Environment.ToolWindowBackground`  
  
 Border  
  
 `Environment.ToolWindowBorder`  
  
 **С плавающей запятой: с фокусом ввода**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Окно инструментов в фокусе](../../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 090_ToolWindowFocused")  
  
 Фон  
  
 `Environment.ToolWindowBackground`  
  
 Border  
  
 `Environment.MainWindowActiveDefaultBorder`  
  
 **С плавающей запятой: без фокуса ввода**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Окно инструментов без фокуса ввода](../../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 091_ToolWindowUnfocused")  
  
 Фон  
  
 `Environment.ToolWindowBackground`  
  
 Border  
  
 `Environment.MainWindowInactiveBorder`  
  
### <a name="tool-window-title-bar"></a>Заголовок окна инструментов  
 Граница заголовка окна является, по сути, не границей, а толстой линией по верхнему краю заголовка. Она не имеет имени токена для состояния без фокуса ввода.  
  
 ![Красная линия заголовок окна инструментов](../../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")  
  
 Используйте:  
 при создании пользовательского интерфейса, соответствующего окнам инструментов.  
  
 Не используйте:  
 для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
 **С фокусом ввода**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Строки заголовка с фокусом ввода](../../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 093_TitleBarFocused")  
  
 **Строки заголовка с фокусом ввода**  
  
 Фон  
  
 `Environment.TitleBarActiveGradientBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.TitleBarActiveText`  
  
 Border  
  
 `Environment.TitleBarActiveBorder`  
  
 Цвет совпадает с цветом фона.  
  
 Маркер перетаскивания  
  
 `Environment.TitleBarDragHandleActive`  
  
 **Без фокуса ввода**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Строки заголовка без фокуса ввода](../../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 094_TitleBarUnfocused")  
  
 **Строки заголовка без фокуса ввода**  
  
 Фон  
  
 `Environment.TitleBarInactiveGradientBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.TitleBarInactiveText`  
  
 Border  
  
 Н/Д  
  
 Маркер перетаскивания  
  
 `Environment.TitleBarDragHandle`  
  
#### <a name="title-bar-buttons"></a>Кнопки в заголовке окна  
 ![Кнопка панели заголовка красная линия](../../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")  
  
 Используйте:  
 для кнопок в пользовательском интерфейсе, для которых используются токены цветов, связанные с заголовками окон инструментов.  
  
 Не используйте:  
 -   для кнопок, отображаемых в других местах;  
  
-   в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Строка кнопка с фокусом ввода заголовка](../../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")  
  
 **С фокусом ввода**  
  
 Фон  
  
 Н/Д  
  
 Передний план (глиф)  
  
 `Environment.ToolWindowButtonActiveGlyph`  
  
 Border  
  
 Н/Д  
  
 ![Строка не в фокусе кнопки заголовка](../../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")  
  
 **Без фокуса ввода**  
  
 Фон  
  
 Н/Д  
  
 Передний план (глиф)  
  
 `Environment.ToolWindowButtonInactiveGlyph`  
  
 Border  
  
 Н/Д  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Кнопка панели заголовка с фокусом ввода при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")  
  
 **С фокусом ввода**  
  
 Фон  
  
 `Environment.ToolWindowButtonHoverActive`  
  
 Передний план (глиф)  
  
 `Environment.ToolWindowButtonHoverActiveGlyph`  
  
 Border  
  
 `Environment.ToolWindowButtonHoverActiveBorder`  
  
 ![Строка без фокуса ввода при наведении курсора на кнопку заголовка](../../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")  
  
 **Без фокуса ввода**  
  
 Фон  
  
 `Environment.ToolWindowButtonHoverInactive`  
  
 Передний план (глиф)  
  
 `Environment.ToolWindowButtonHoverInactiveGlyph`  
  
 Border  
  
 `Environment.ToolWindowButtonHoverInactiveBorder`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Заголовок панели кнопка с фокусом ввода и нажата](../../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")  
  
 **С фокусом ввода**  
  
 Фон  
  
 `Environment.ToolWindowButtonDown`  
  
 Передний план (глиф)  
  
 `Environment.ToolWindowButtonDownActiveGlyph`  
  
 Border  
  
 `Environment.ToolWindowButtonDownBorder`  
  
 ![Кнопка панели заголовка без фокуса ввода и нажат](../../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")  
  
 **Без фокуса ввода**  
  
 Фон  
  
 `Environment.ToolWindowButtonDown`  
  
 Передний план (глиф)  
  
 `Environment.ToolWindowButtonDownInactiveGlyph`  
  
 Border  
  
 `Environment.ToolWindowButtonDownBorder`  
  
### <a name="tool-window-tabs"></a>Вкладки окна инструментов  
 ![Красная линия вкладки окна инструментов](../../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303 102_ToolWindowTabRedline")  
  
 Используйте:  
 при создании пользовательского интерфейса, соответствующего окнам инструментов.  
  
 Не используйте:  
 для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
 **Выбранная вкладка**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Вкладка окна инструментов с фокусом ввода](../../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")  
  
 **Вкладка окна выбранных инструментов с фокусом ввода**  
  
 Фон  
  
 `Environment.ToolWindowTabSelectedTab`  
  
 Передний план (текст)  
  
 `Environment.ToolWindowTabSelectedActiveText`  
  
 Border  
  
 `Environment.ToolWindowTabSelectedBorder`  
  
 Цвет совпадает с цветом фона.  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Вкладка окна инструментов без фокуса ввода](../../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")  
  
 **Вкладка окна выбранных инструментов без фокуса ввода**  
  
 Фон  
  
 `Environment.ToolWindowTabSelectedTab`  
  
 Передний план (текст)  
  
 `Environment.ToolWindowTabSelectedText`  
  
 Border  
  
 `Environment.ToolWindowTabSelectedBorder`  
  
 Цвет совпадает с цветом фона.  
  
 **Вкладка фона**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Вкладка фона окна инструментов](../../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")  
  
 **Фоновая вкладка окна инструментов**  
  
 Фон  
  
 `Environment.ToolWindowTabGradientBegin`  
  
 Ограничения градиента устанавливаются в Visual Studio 2013 в то же значение цвета.  
  
 `Environment.ToolWindowTabGradientEnd`  
  
 Ограничения градиента устанавливаются в Visual Studio 2013 в то же значение цвета.  
  
 Передний план (текст)  
  
 `Environment.ToolWindowTabText`  
  
 Border  
  
 `Environment.ToolWindowTabBorder`  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Вкладка фона окна инструментов при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")  
  
 **Фоновая вкладка окна инструментов при наведении курсора мыши**  
  
 Фон  
  
 `Environment.ToolWindowTabMouseOverBackgroundBegin`  
  
 Ограничения градиента устанавливаются в Visual Studio 2013 в то же значение цвета.  
  
 `Environment.ToolWindowTabMouseOverBackgroundEnd`  
  
 Ограничения градиента устанавливаются в Visual Studio 2013 в то же значение цвета.  
  
 Передний план (текст)  
  
 `Environment.ToolWindowTabMouseOverText`  
  
 Border  
  
 `Environment.ToolWindowTabMouseOverBorder`  
  
 Цвет совпадает с цветом фона.  
  
### <a name="auto-hide-tabs"></a>Автоматически скрываемые вкладки  
 ![Автоматическое&#45;красная линия скрыть](../../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303 107_AutoHideRedline")  
  
 Используйте:  
 при создании пользовательского интерфейса, соответствующего автоматически скрываемым вкладкам окна инструментов.  
  
 Не используйте:  
 для пользовательского интерфейса, который не должен обновляться автоматически при изменении темы оболочки.  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Автоматическое&#45;скрыть вкладку](../../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 108_AutoHideTab")  
  
 **Автоматически скрываемая вкладка по умолчанию**  
  
 Фон  
  
 `Environment.AutoHideTabBackgroundBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.AutoHideTabText`  
  
 Border  
  
 `Environment.AutoHideTabBorder`  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Автоматическое&#45;скрыть вкладку при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 109_AutoHideTabHover")  
  
 **Вкладка автоматического скрытия при наведении курсора мыши**  
  
 Фон  
  
 `Environment.AutoHideTabMouseOverBackgroundBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `Environment.AutoHideTabMouseOverText`  
  
 Border  
  
 `Environment.AutoHideTabMouseOverBorder`  
  
## <a name="common-shared-controls"></a>Стандартные общие элементы управления  
 При использовании в компоненте стандартной панели команд Visual Studio вы имеете доступ к оформленным элементам управления оболочки. Изменять шаблон этих стандартных элементов управления не следует. Однако если вам нужно создать пользовательскую панель команд, вам также может потребоваться создать пользовательские элементы управления. В этом случае используйте правильные имена токенов для каждого из указанных ниже элементов управления, чтобы ваш пользовательский интерфейс был согласован с остальной средой Visual Studio.  
  
### <a name="search-box"></a>Поле поиска  
 По возможности используйте стандартный элемент управления поиском, предоставляемый средой Visual Studio. Цвета поля поиска находятся в категории SearchControl в файле **ShellColors.pkgdef** , который содержит имена токенов для поля ввода, управляющей кнопки, кнопки раскрывающегося списка и раскрывающегося меню.  
  
 Поле поиска может находиться в одном из нескольких состояний. Некоторые из них взаимоисключающие.  
  
-   "С фокусом ввода" или "без фокуса ввода" указывает на то, находится ли курсор в текстовом поле.  
  
-   "Активно" или "неактивно" указывает на то, ввел ли пользователь запрос в текстовом поле.  
  
-   "При наведении указателя" означает, что пользователь навел указатель мыши на поле поиска (это состояние переопределяет все остальные).  
  
-   "Отключено" означает, что функция поиска в текущем контексте отключена.  
  
 ![Красная линия окна поиска](../../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303 110_SearchBoxRedline")  
  
 Используйте:  
 при разработке пользовательского поля поиска.  
  
 Не используйте:  
 -   для любого элемента, не являющегося полем поиска;  
  
-   для любого элемента, который не должен всегда соответствовать пользовательскому интерфейсу поля поиска.  
  
 **С фокусом ввода**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Поле ввода окна поиска с фокусом ввода](../../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")  
  
 **Поле ввода**  
  
 Фон  
  
 `SearchControl.FocusedBackground`  
  
 Передний план (текст)  
  
 `SearchControl.FocusedBackground`  
  
 Border  
  
 `SearchControl.FocusedBorder`  
  
 Separator  
  
 `SearchControl.FocusedDropDownSeparator`  
  
 ![Кнопка поиска с фокусом ввода](../../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")  
  
 **Управляющая кнопка**  
  
 Фон  
  
 Нет  
  
 Передний план (глиф поиска)  
  
 `SearchControl.SearchGlyph`  
  
 Передний план (глиф остановки)  
  
 `SearchControl.StopGlyph`  
  
 Передний план (глиф очистки)  
  
 `SearchControl.ClearGlyph`  
  
 Border  
  
 Н/Д  
  
 ![Search drop&#45;кнопка с фокусом ввода вниз](../../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")  
  
 **Кнопка раскрывающегося списка**  
  
 Фон  
  
 `SearchControl.FocusedDropDownButton`  
  
 Передний план (глиф)  
  
 `SearchControl.FocusedDropDownButtonGlyph`  
  
 Border  
  
 `SearchControl.FocusedDropDownButtonBorder`  
  
 **Без фокуса ввода**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Поле ввода окна поиска без фокуса ввода](../../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")  
  
 **Активное поле ввода**  
  
 Фон  
  
 `SearchControl.SearchActiveBackground`  
  
 Передний план (текст)  
  
 `SearchControl.SearchActiveBackground`  
  
 Border  
  
 `SearchControl.UnfocusedBorder`  
  
 Separator  
  
 `SearchControl.DropDownSeparator`  
  
 ![Поле ввода окна поиска без фокуса ввода и неактивные](../../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")  
  
 **Неактивное поле ввода**  
  
 Фон  
  
 `SearchControl.Unfocused`  
  
 Передний план (текст)  
  
 `SearchControl.Unfocused`  
  
 Border  
  
 `SearchControl.UnfocusedBorder`  
  
 Separator  
  
 `SearchControl.DropDownSeparator`  
  
 ![Кнопка поиска без фокуса ввода](../../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")  
  
 **Управляющая кнопка**  
  
 Фон  
  
 Н/Д  
  
 Передний план (глиф поиска)  
  
 `SearchControl.SearchGlyph`  
  
 Передний план (глиф остановки)  
  
 `SearchControl.StopGlyph`  
  
 Передний план (глиф очистки)  
  
 `SearchControl.ClearGlyph`  
  
 Border  
  
 Н/Д  
  
 ![Search drop&#45;нажатой кнопку без фокуса ввода](../../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")  
  
 **Кнопка раскрывающегося списка**  
  
 Фон  
  
 `SearchControl.UnfocusedDropDownButton`  
  
 Передний план (глиф)  
  
 `SearchControl.UnfocusedDropDownButtonGlyph`  
  
 Border  
  
 `SearchControl.UnfocusedDropDownButtonBorder`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Нажата кнопка поиска](../../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")  
  
 **Управляющая кнопка**  
  
 Фон  
  
 `SearchControl.ActionButtonMouseDown`  
  
 Передний план (глиф)  
  
 `SearchControl.ActionButtonMouseDownGlyph`  
  
 Border  
  
 `SearchControl.ActionButtonMouseDownBorder`  
  
 ![Search drop&#45;вниз была нажата кнопка](../../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")  
  
 **Кнопка раскрывающегося списка**  
  
 Фон  
  
 `SearchControl.MouseDownDropDownButton`  
  
 Передний план (глиф)  
  
 `SearchControl.MouseDownDropDownButtonGlyph`  
  
 Border  
  
 `SearchControl.MouseDownDropDownButtonBorder`  
  
 **Выделено (только текст)**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Выделение поля ввода окна поиска](../../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")  
  
 **Поле ввода с выделенным текстом**  
  
 Фон  
  
 `SearchControl.Selection`  
  
 Передний план (текст)  
  
 `SearchControl.FocusedBackground`  
  
 Border  
  
 Нет  
  
 Separator  
  
 `SearchControl.FocusedDropDownSeparator`  
  
 **Отключено**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Поле ввода окна поиска отключена](../../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")  
  
 **Поле ввода**  
  
 Фон  
  
 `SearchControl.Disabled`  
  
 Передний план (текст)  
  
 `SearchControl.Disabled`  
  
 Border  
  
 `SearchControl.DisabledBorder`  
  
 Separator  
  
 `SearchControl.DropDownSeparator`  
  
 ![Неактивная кнопка поиска](../../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")  
  
 **Управляющая кнопка**  
  
 Фон  
  
 Нет  
  
 Передний план (глиф)  
  
 `SearchControl.ActionButtonDisabledGlyph`  
  
 Border  
  
 Нет  
  
 ![Search drop&#45;вниз неактивная кнопка](../../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")  
  
 **Кнопка раскрывающегося списка**  
  
 Фон  
  
 Нет  
  
 Передний план (глиф)  
  
 `SearchControl.DisabledDownButtonGlyph`  
  
 Border  
  
 Нет  
  
#### <a name="search-drop-down-lists"></a>Раскрывающиеся списки поиска  
 Раскрывающиеся меню в поле поиска могут быть немного более сложными, чем другие раскрывающиеся меню в Visual Studio. Разделы "предлагаемые запросы поиска" и "параметры поиска" могут присутствовать в меню вместе или по отдельности. Каждый из них имеет особые цвета. Если имеются оба этих раздела, они разделяются линией, а все раскрывающееся меню окружено границей.  
  
 ![Search drop&#45;вниз красная линия](../../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303 124_SearchDropdownRedline")  
  
 Используйте:  
 -   при создании пользовательского раскрывающегося списка поиска;  
  
-   правильные имена токенов для соответствующих компонентов списка.  
  
 Не используйте:  
 -   для раскрывающихся списков, которые используются в других контекстах;  
  
-   в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.  
  
 **По умолчанию (нет других состояний)**  
  
 Элемент  
  
 Имя токена: Category.color  
  
 Border  
  
 `SearchControl.PopupBorder`  
  
 Separator  
  
 `SearchControl.PopupSectionHeaderSeparator`  
  
 Тень  
  
 `Environment.DropShadowBackground`  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Предлагаемый поиск](../../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 125_SearchSuggested")  
  
 **Предлагаемые запросы поиска**  
  
 Фон  
  
 `SearchControl.PopupItemsListBackgroundGradientBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `SearchControl.PopupItemText`  
  
 ![Флажок поиска](../../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")  
  
 **Параметры поиска (флажок)**  
  
 ![Параметры поиска](../../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")  
  
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
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Предлагаемый при наведении курсора мыши поиск](../../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 128_SearchSuggestedHover")  
  
 **Предлагаемые запросы поиска**  
  
 Фон  
  
 `SearchControl.PopupControlMouseOverBackgroundGradientBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст)  
  
 `SearchControl.PopupMouseOverItemText`  
  
 Border  
  
 `SearchControl.PopupControlMouseOverBorder`  
  
 ![Флажок поиска при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 129_SearchCheckboxHover")  
  
 **Предлагаемые запросы поиска (флажок)**  
  
 ![Параметры при наведении курсора мыши поиска](../../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 130_SearchOptionsHover")  
  
 **Параметры поиска**  
  
 Фон  
  
 `SearchControl.PopupControlMouseOverBackgroundGradientBegin`  
  
 Хотя этот цвет фона не используется в современной теме пользовательского интерфейса, для него заданы значения и ограничения градиента.  
  
 Передний план (текст флажка)  
  
 `SearchControl.PopupCheckboxMouseDownText`  
  
 Передний план (текст ссылки)  
  
 `SearchControl.PopupButtonMouseDownText`  
  
 Border  
  
 `SearchControl.PopupControlMouseOverBorder`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Активный предлагаемый поиск](../../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")  
  
 **Предлагаемые запросы поиска (флажок)**  
  
 ![Активные параметры поиска](../../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")  
  
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
  
 ![Красная линия гиперссылки](../../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303 133_HyperlinkRedline")  
  
 Используйте:  
 если нужно создать пользовательскую гиперссылку.  
  
 Не используйте:  
 для любого элемента, не являющегося гиперссылкой.  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Гиперссылка по умолчанию](../../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303 134_Hyperlink")  
  
 Передний план (текст)  
  
 `Environment.PanelHyperlink`  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Гиперссылка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303 135_HyperlinkHover")  
  
 Передний план (текст)  
  
 `Environment.PanelHyperlinkHover`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Активная гиперссылка](../../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303 136_HyperlinkPressed")  
  
 Передний план (текст)  
  
 `Environment.PanelHyperlinkPressed`  
  
 **Отключено**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Неактивная гиперссылка](../../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303 137_HyperlinkDisabled")  
  
 Передний план (текст)  
  
 `Environment.PanelHyperlinkDisabled`  
  
### <a name="infobar"></a>Информационная панель  
 Информационные панели служат для предоставления дополнительной информации о данном контексте и всегда отображаются в верхней части окна документа или окна инструментов.  
  
 ![Красная линия информационной панели](../../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303 138_InfobarRedline")  
  
 Используйте:  
 при создании пользовательских информационных панелей.  
  
 Не используйте:  
 для элементов пользовательского интерфейса, которые не похожи на информационную панель.  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Информационная панель](../../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 139_Infobar")  
  
 **Информационная панель**  
  
 Фон  
  
 `Environment.InfoBackground`  
  
 Передний план (текст)  
  
 `Environment.InfoText`  
  
 Border  
  
 `Environment.ToolWindowBorder`  
  
### <a name="scroll-bar"></a>Полоса прокрутки  
 Полосы прокрутки оформляются средой Visual Studio, и применять к ним темы не нужно. Тем не менее вы решите, что вы хотите использовать цвета, применяемые в полосах прокрутки, чтобы пользовательский Интерфейс был согласован с этой частью среды Visual Studio.  
  
 ![Красная линия полосы прокрутки](../../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303 140_ScrollbarRedline")  
  
 Используйте:  
 при создании пользовательского интерфейса, который должен соответствовать полосам прокрутки Visual Studio.  
  
 Не используйте:  
 для каких-либо элементов, которые не должны всегда соответствовать пользовательскому интерфейсу полос прокрутки.  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Полоса прокрутки](../../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 141_Scrollbar")  
  
 **Полосы прокрутки**  
  
 Полоса прокрутки  
  
 `Environment.ScrollBarBackground`  
  
 Передний план (бегунок)  
  
 `Environment.ScrollBarThumbBackground`  
  
 ![Полоса стрелку прокрутки](../../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 142_ScrollbarArrow")  
  
 **Стрелка прокрутки**  
  
 Фон  
  
 `Environment.ScrollBarArrowBackground`  
  
 Цвет совпадает с цветом полосы прокрутки.  
  
 Передний план (глиф)  
  
 `Environment.ScrollBarArrowGlyph`  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Полосы прокрутки при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 143_ScrollbarHover")  
  
 **Полосы прокрутки**  
  
 Полоса прокрутки  
  
 `Environment.ScrollBarBackground`  
  
 Передний план (бегунок)  
  
 `Environment.ScrollBarThumbMouseOverBackground`  
  
 ![Прокрутите панель со стрелками при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 144_ScrollbarArrowHover")  
  
 **Стрелка прокрутки**  
  
 Фон  
  
 `Environment.ScrollBarArrowMouseOverBackground`  
  
 Цвет совпадает с цветом полосы прокрутки.  
  
 Передний план (глиф)  
  
 `Environment.ScrollBarArrowGlyphMouseOver`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Полоса прокрутки нажата](../../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 145_ScrollbarPressed")  
  
 **Полосы прокрутки**  
  
 Полоса прокрутки  
  
 `Environment.ScrollBarBackground`  
  
 Передний план (бегунок)  
  
 `Environment.ScrollBarThumbPressedBackground`  
  
 ![Полоса нажатой стрелки прокрутки](../../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")  
  
 **Стрелка прокрутки**  
  
 Фон  
  
 `Environment.ScrollBarArrowPressedBackground`  
  
 Цвет совпадает с цветом полосы прокрутки.  
  
 Передний план (глиф)  
  
 `Environment.ScrollBarArrowGlyphPressed`  
  
###  <a name="BKMK_TreeView"></a> Представление в виде дерева  
 В некоторых окнах инструментов, включая обозреватель решений, обозреватель сервера и представление классов, реализована иерархическая организационная схема, цвета которой определяются названиями цветов в категории TreeView. Все элементы в иерархическом представлении имеют цвета фона и текста. Элементы с вложенными дочерними элементами также имеют глифы, которые указывают на то, является ли элемент свернутым или развернутым.  
  
 ![Красная линия дерева](../../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303 147_TreeViewRedline")  
  
 Используйте:  
 если необходимо реализовать иерархическое представление.  
  
 Не используйте:  
 -   для каких-либо элементов, отличных от иерархического представления;  
  
-   в каком-либо сочетании цвета фона и цвета переднего плана, отличном от определенных.  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Представление в виде дерева](../../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 148_TreeView")  
  
 Фон  
  
 `TreeView.Background`  
  
 Передний план (текст)  
  
 `TreeView.Background`  
  
 Передний план (глиф)  
  
 `TreeView.Glyph`  
  
 Border  
  
 Нет  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Представление при наведении курсора мыши в виде дерева](../../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 149_TreeViewHover")  
  
 Фон  
  
 `TreeView.Background`  
  
 Передний план (текст)  
  
 `TreeView.Background`  
  
 Передний план (глиф)  
  
 `TreeView.GlyphMouseOver`  
  
 Border  
  
 Нет  
  
 **Перетащите**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Перетаскивание представления в виде дерева](../../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 150_TreeViewDragOver")  
  
 Фон  
  
 `TreeView.DragOverItem`  
  
 Передний план (текст)  
  
 `TreeView.DragOverItem`  
  
 Передний план (глиф)  
  
 `TreeView.DragOverItemGlyph`  
  
 Border  
  
 Нет  
  
 **Выбранные**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Представление с фокусом ввода в виде дерева](../../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 151_TreeViewFocused")  
  
 **С фокусом ввода**  
  
 Фон  
  
 `TreeView.SelectedItemActive`  
  
 Передний план (текст)  
  
 `TreeView.SelectedItemActive`  
  
 Передний план (глиф)  
  
 `TreeView.SelectedItemActiveGlyph`  
  
 Border  
  
 `TreeView.FocusVisualBorder`  
  
 ![Представление без фокуса ввода в виде дерева](../../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 152_TreeViewUnfocused")  
  
 **Без фокуса ввода**  
  
 Фон  
  
 `TreeView.SelectedItemInactive`  
  
 Передний план (текст)  
  
 `TreeView.SelectedItemInactive`  
  
 Передний план (глиф)  
  
 `TreeView.SelectedItemInactiveGlyph`  
  
 Border  
  
 Нет  
  
 **Наведите указатель мыши выбранные**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Представление, с фокусом ввода при наведении курсора мыши в виде дерева](../../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")  
  
 **С фокусом ввода**  
  
 Фон  
  
 `TreeView.SelectedItemActive`  
  
 Передний план (текст)  
  
 `TreeView.SelectedItemActive`  
  
 Передний план (глиф)  
  
 `TreeView.SelectedItemActiveGlyphMouseOver`  
  
 Border  
  
 Нет`TreeView.FocusVisualBorder`  
  
 ![Представление без фокуса ввода при наведении курсора мыши в виде дерева](../../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")  
  
 **Без фокуса ввода**  
  
 Фон  
  
 `TreeView.SelectedItemInactive`  
  
 Передний план (текст)  
  
 `TreeView.SelectedItemInactive`  
  
 Передний план (глиф)  
  
 `TreeView.SelectedItemActiveGlyphMouseOver`  
  
 Border  
  
 Нет  
  
### <a name="button-controls"></a>Элементы управления "Кнопка"  
 ![Красная линия управления "Кнопка"](../../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303 155_ButtonControlRedline")  
  
 Используйте:  
 для кнопок в контейнере документа, которые должны интегрироваться с темами Visual Studio (светлая, темная, синяя или системная высококонтрастная тема).  
  
 Не используйте:  
 для кнопок, которые будут отображаться на пользовательском фоне, не входящем в тему Visual Studio.  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Кнопка](../../extensibility/ux-guidelines/media/0303-156-button.png "0303 156_Button")  
  
 Кнопка  
  
 `CommonControls.Button`  
  
 Граница кнопки  
  
 `CommonControls.ButtonBorder`  
  
 **Отключено**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Кнопка отключена](../../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 157_ButtonDisabled")  
  
 Кнопка  
  
 `CommonControls.ButtonDisabled`  
  
 Граница кнопки  
  
 `CommonControls.ButtonBorderDisabled`  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Кнопка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 158_ButtonHover")  
  
 Кнопка  
  
 `CommonControls.ButtonHover`  
  
 Граница кнопки  
  
 `CommonControls.ButtonBorderHover`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Была нажата кнопка](../../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 159_ButtonPressed")  
  
 Кнопка  
  
 `CommonControls.ButtonPressed`  
  
 Граница кнопки  
  
 `CommonControls.ButtonBorderPressed`  
  
 **С фокусом ввода**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Кнопка с фокусом ввода](../../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 160_ButtonFocused")  
  
 Кнопка  
  
 `CommonControls.ButtonFocused`  
  
 Граница кнопки  
  
 `CommonControls.ButtonBorderFocused`  
  
### <a name="check-box-controls"></a>Элементы управления "Флажок"  
 ![Красная линия флажка](../../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303 161_CheckboxRedline")  
  
 Используйте:  
 для элементов управления типа "Флажок", содержащихся в контейнере документа.  
  
 Не используйте:  
 для пользовательского интерфейса, который не является элементом управления "Флажок".  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Флажок](../../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 162_Checkbox")  
  
 Фон  
  
 `CommonControls.CheckBoxBackground`  
  
 Border  
  
 `CommonControls.CheckBoxBorder`  
  
 Текста  
  
 `CommonControls.CheckBoxText`  
  
 Глиф  
  
 `CommonControls.CheckBoxGlyph`  
  
 **Отключено**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Неактивный флажок](../../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 163_CheckboxDisabled")  
  
 Фон  
  
 `CommonControls.CheckBoxBackgroundDisabled`  
  
 Border  
  
 `CommonControls.CheckBoxBorderDisabled`  
  
 Текста  
  
 `CommonControls.CheckBoxTextDisabled`  
  
 Глиф  
  
 `CommonControls.CheckBoxGlyphDisabled`  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Флажок при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 164_CheckboxHover")  
  
 Фон  
  
 `CommonControls.CheckBoxBackgroundHover`  
  
 Border  
  
 `CommonControls.CheckBoxBorderHover`  
  
 Текста  
  
 `CommonControls.CheckBoxTextHover`  
  
 Глиф  
  
 `CommonControls.CheckBoxGlyphHover`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Активный флажок](../../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 165_CheckboxPressed")  
  
 Фон  
  
 `CommonControls.CheckBoxBackgroundPressed`  
  
 Border  
  
 `CommonControls.CheckBoxBorderPressed`  
  
 Текста  
  
 `CommonControls.CheckBoxTextPressed`  
  
 Глиф  
  
 `CommonControls.CheckBoxGlyphPressed`  
  
 **С фокусом ввода**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Флажок с фокусом ввода](../../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 166_CheckboxFocused")  
  
 Фон  
  
 `CommonControls.CheckBoxBackgroundFocused`  
  
 Border  
  
 `CommonControls.CheckBoxBorderFocused`  
  
 Текста  
  
 `CommonControls.CheckBoxTextFocused`  
  
 Глиф  
  
 `CommonControls.CheckBoxGlyphFocused`  
  
### <a name="drop-boxcombo-box-controls"></a>Элементы управления "Раскрывающийся список" и "Поле со списком"  
 ![DROP&#45;вниз&#47;красная линия со списком](../../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303 167_DropDownComboBoxRedline")  
  
 Используйте:  
 для раскрывающихся списков и полей со списком, которые являются частью контейнера документа.  
  
 Не используйте:  
 -   для других элементов пользовательского интерфейса, не являющихся раскрывающимися списками или полями со списком;  
  
-   для [Drop-down](../../misc/shared-colors.md#BKMK_CommandDropDown) или [Combo box](../../misc/shared-colors.md#BKMK_CommandComboBox) на панели команд.  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![DROP&#45;вниз&#47;поле со списком](../../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")  
  
 Фон  
  
 `CommonControls.ComboBoxBackground`  
  
 Border  
  
 `CommonControls.ComboBoxBorder`  
  
 Текста  
  
 `CommonControls.ComboBoxText`  
  
 Separator  
  
 `CommonControls.ComboBoxSeparator`  
  
 Глиф  
  
 `CommonControls.ComboBoxGlyph`  
  
 Фон глифа  
  
 `CommonControls.ComboBoxGlyphBackground`  
  
 **Отключено**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![DROP&#45;вниз&#47;отключенного поля со списком](../../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")  
  
 Фон  
  
 `CommonControls.ComboBoxBackgroundDisabled`  
  
 Border  
  
 `CommonControls.ComboBoxBorderDisabled`  
  
 Текста  
  
 `CommonControls.ComboBoxTextDisabled`  
  
 Separator  
  
 `CommonControls.ComboBoxSeparatorDisabled`  
  
 Глиф  
  
 `CommonControls.ComboBoxGlyphDisabled`  
  
 Фон глифа  
  
 `CommonControls.ComboBoxGlyphBackgroundDisabled`  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![DROP&#45;вниз&#47;поле со списком при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")  
  
 Фон  
  
 `CommonControls.ComboBoxBackgroundHover`  
  
 Border  
  
 `CommonControls.ComboBoxBorderHover`  
  
 Текста  
  
 `CommonControls.ComboBoxTextHover`  
  
 Separator  
  
 `CommonControls.ComboBoxSeparatorHover`  
  
 Глиф  
  
 `CommonControls.ComboBoxGlyphHover`  
  
 Фон глифа  
  
 `CommonControls.ComboBoxGlyphBackgroundHover`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![DROP&#45;вниз&#47;поле со списком при нажатии](../../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")  
  
 Фон  
  
 `CommonControls.ComboBoxBackgroundPressed`  
  
 Border  
  
 `CommonControls.ComboBoxBorderPressed`  
  
 Текста  
  
 `CommonControls.ComboBoxTextPressed`  
  
 Separator  
  
 `CommonControls.ComboBoxSeparatorPressed`  
  
 Глиф  
  
 `CommonControls.ComboBoxGlyphPressed`  
  
 Фон глифа  
  
 `CommonControls.ComboBoxGlyphBackgroundPressed`  
  
 **С фокусом ввода**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![DROP&#45;вниз&#47;поле со списком с фокусом ввода](../../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")  
  
 Фон  
  
 `CommonControls.ComboBoxBackgroundFocused`  
  
 Border  
  
 `CommonControls.ComboBoxBorderFocused`  
  
 Текста  
  
 `CommonControls.ComboBoxTextFocused`  
  
 Separator  
  
 `CommonControls.ComboBoxSeparatorFocused`  
  
 Глиф  
  
 `CommonControls.ComboBoxGlyphFocused`  
  
 Фон глифа  
  
 `CommonControls.ComboBoxGlyphBackgroundFocused`  
  
 **Входной выделенного текста**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![DROP&#45;вниз&#47;текстового поля со списком ввода](../../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303 173_DropDownComboBoxTextInput")  
  
 Выделение  
  
 `CommonControls.ComboBoxTextInputSelection`  
  
 **Активный — представление элемента списка**  
  
 ![DROP&#45;вниз&#47;представление списка в поле со списком](../../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")  
  
 Фон  
  
 `CommonControls.ComboBoxListBackground`  
  
 `CommonControls.ComboBoxListBackgroundHover`  
  
 `CommonControls.ComboBoxListItemBackgroundPressed`  
  
 `CommonControls.ComboBoxListItemBackgroundFocused`  
  
 Border  
  
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
  
 ![Табличные данные &#40;сетку&#41; красная линия](../../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")  
  
 Используйте:  
 для табличных элементов управления или элементов управления "Сетка".  
  
 Не используйте:  
 для элементов пользовательского интерфейса, которые не являются табличными элементами управления или элементами управления "Сетка".  
  
#### <a name="column-headers"></a>Заголовки столбцов  
 Заголовки столбцов состоят из фона, границы, текста заголовка и необязательного глифа, который обычно используется при сортировке сетки по данному столбцу.  
  
 Регион  
  
 Элемент  
  
 Имя токена: Category.color  
  
 Значение по умолчанию  
  
 Фон  
  
 `Header.Default`  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextActive`  
  
 Передний план (глиф)  
  
 `Header.Glyph`  
  
 Border  
  
 `Header.SeparatorLine`  
  
 Наведение  
  
 Фон  
  
 `Header.MouseOver`  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextHover`  
  
 Передний план (глиф)  
  
 `Header.MouseOverGlyph`  
  
 Border  
  
 `Header.SeparatorLine`  
  
 Нажато  
  
 Фон  
  
 `CommonControls.CheckBoxBackgroundPressed`  
  
 Передний план (текст)  
  
 `CommonControls.CheckBoxBorderPressed`  
  
 Передний план (глиф)  
  
 `CommonControls.CheckBoxTextPressed`  
  
 Border  
  
 `CommonControls.CheckBoxGlyphPressed`  
  
#### <a name="list-view-items"></a>Элементы представления списка  
 Элементы представления списка состоят из фона и содержимого. Содержимым может быть текст, значок или и то и другое.  
  
 Регион  
  
 Элемент  
  
 Имя токена: Category.color  
  
 Значение по умолчанию  
  
 Фон  
  
 Прозрачный  
  
 Передний план (текст)  
  
 `Environment.CommandBarTextActive`  
  
 Border  
  
 Нет  
  
 Выбран (активен)  
  
 Фон  
  
 `TreeView.SelectedItemActive`  
  
 Передний план (текст)  
  
 `TreeView.SelectedItemActiveText`  
  
 Border  
  
 Нет  
  
 Выбран (неактивен)  
  
 Фон  
  
 `TreeView.SelectedItemInactive`  
  
 Передний план (текст)  
  
 `TreeView.SelectedItemInactiveText`  
  
 Border  
  
 Нет  
  
## <a name="manifest-designer"></a>Конструктор манифеста  
 Конструктор манифеста призван упростить редактирование файла манифеста в проектах Windows 8 и Windows Phone 8. Хотя общего готового шаблона нет, рекомендуется обеспечивать соответствие макету и цветам вкладок ориентации и навигации, а также общей структуре. Дополнительные сведения о макете см. в разделе [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![Красная линия конструктора манифеста](../../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303 175_ManifestDesignerRedline")  
  
 Используйте:  
 -   для конструкторов, которые похожи на конструктор манифеста;  
  
-   вместо использования стандартных элементов управления типа "Вкладка" в верхней части редактора в контейнере документа.  
  
 Не используйте:  
 -   при наличии более чем шести вкладок;  
  
-   для пользовательского интерфейса, который отличается структурой от конструктора манифеста.  
  
 Регион  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 По умолчанию (выбрано)  
  
 Tab  
  
 Фон  
  
 `ManifestDesigner.TabActive`  
  
 Border  
  
 Нет  
  
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
  
 Tab  
  
 Фон  
  
 `ManifestDesigner.Tab.Inactive`  
  
 Наведение  
  
 Tab  
  
 Фон  
  
 `ManifestDesigner.Tab.Mouseover`  
  
## <a name="tagging"></a>Добавление тегов  
 Visual Studio поддерживает добавление тегов, что позволяет пользователю объявлять доступные для поиска ключевые слова в целях отслеживания. Например, руководители проектов и разработчики могут использовать Team Foundation Server (TFS) для добавления тегов к рабочим элементам. В приведенных ниже таблицах представлены имена цветов как для самого тега, так и для глифа (значка закрытия), который появляется при наведении указателя и в некоторых состояниях.  
  
 ![Красная линия пометки тегами](../../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303 176_TaggingRedline")  
  
 Используйте:  
 для пользовательского интерфейса, который поддерживает добавление тегов.  
  
 Не используйте:  
 для любого другого пользовательского интерфейса.  
  
### <a name="tag"></a>Тег  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Тег](../../extensibility/ux-guidelines/media/0303-177-tag.png "0303 177_Tag")  
  
 **Default**  
  
 Фон  
  
 `Tag.Background`  
  
 Передний план (текст)  
  
 `Tag.Background`  
  
 ![Тег при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 178_TagHover")  
  
 **При наведении курсора мыши**  
  
 Фон  
  
 `Tag.HoverBackground`  
  
 Передний план (текст)  
  
 `Tag.HoverBackgroundText`  
  
 ![Активный тег](../../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 179_TagPressed")  
  
 **Нажата**  
  
 Фон  
  
 `Tag.PressedBackground`  
  
 Передний план (текст)  
  
 `Tag.PressedBackgroundText`  
  
 ![Выбранный тег](../../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 180_TagSelected")  
  
 **Выбранные**  
  
 Фон  
  
 `Tag.SelectedBackground`  
  
 Передний план (текст)  
  
 `Tag.SelectedBackgroundText`  
  
### <a name="glyph-close-icon"></a>Глиф (значок закрытия)  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Тег &#40;глиф&#41;](../../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 181_TagGlyph")  
  
 **По умолчанию (тег по умолчанию)**  
  
 Фон  
  
 Н/Д  
  
 Передний план (глиф)  
  
 `Tag.TagHoverGlyph`  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Тег &#40;глиф&#41; при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 182_TagGlyphHover")  
  
 **При наведении указателя мыши (тег по умолчанию)**  
  
 Фон  
  
 `Tag.TagHoverGlyphHoverBackground`  
  
 Передний план (глиф)  
  
 `Tag.TagHoverGlyphHover`  
  
 Border  
  
 `Tag.TagHoverGlyphHoverBorder`  
  
 **Нажата**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Тег &#40;глиф&#41; нажата](../../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 183_TagGlyphPressed")  
  
 **Нажата (тег по умолчанию)**  
  
 Фон  
  
 `Tag.TagHoverGlyphPressedBackground`  
  
 Передний план (глиф)  
  
 `Tag.TagHoverGlyphPressed`  
  
 Border  
  
 `Tag.TagHoverGlyphPressedBorder`  
  
 **Тег выбран/глиф по умолчанию**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Выбранный тег](../../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 184_TagSelected")  
  
 **По умолчанию (тег выбран)**  
  
 Фон  
  
 Н/Д  
  
 Передний план (глиф)  
  
 `Tag.TagSelectedGlyph`  
  
 **Тег выбран/глиф при наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Выбранный тег при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 185_TagSelectedHover")  
  
 **При наведении указателя мыши (тег выбран)**  
  
 Фон  
  
 `Tag.TagSelectedGlyphHoverBackground`  
  
 Передний план (глиф)  
  
 `Tag.TagSelectedGlyphHover`  
  
 Border  
  
 `Tag.TagSelectedGlyphHoverBorder`  
  
 **Тег выбран/активный глиф**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Выбранный тег нажата](../../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 186_TagSelectedPressed")  
  
 **Активен (тег выбран)**  
  
 Фон  
  
 `Tag.TagSelectedGlyphPressedBackground`  
  
 Передний план (глиф)  
  
 `Tag.TagSelectedGlyphPressed`  
  
 Border  
  
 `Tag.TagSelectedGlyphPressedBorder`  
  
## <a name="shell"></a>Оболочка  
  
### <a name="background"></a>Фон  
 Фон среды состоит из двух слоев. Нижний слой представляет собой сплошной цвет, который охватывает всю интегрированную среду разработки. Верхний слой используется под командной полкой и между каналами автоматического скрытия окон инструментов по левому и правому краям интегрированной среды разработки. Начиная с версии Visual Studio 2013 верхний и нижний слои фона имеют одинаковый цвет при использовании светлой и темной тем.  
  
 ![Красная линия фоновой оболочки](../../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303 187_ShellBackgroundRedline")  
  
 Используйте:  
 для областей, которые должны соответствовать фону среды Visual Studio.  
  
 Не используйте:  
 -   в качестве заливки для областей, которые не являются фоновыми;  
  
-   в качестве фона, на котором должны размещаться элементы переднего плана.  
  
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
  
 *Ограничения градиента устанавливаются в одно и то же значение цвета в Visual Studio 2013 светлой и темной тем.*  
  
 `Environment.EnvironmentBackgroundGradientBegin`  
  
 `Environment.EnvironmentBackgroundGradientEnd`  
  
 `Environment.EnvironmentBackgroundGradientMiddle1`  
  
 `Environment.EnvironmentBackgroundGradientMiddle2`  
  
### <a name="command-shelf"></a>Командная полка  
 Для фона командной полки используются два набора имен токенов: один для области размещения строки меню, а другой — для области размещения панелей команд. Отдельные группы на панели команд имеют собственные значения цветов фона, которые более подробно рассматриваются в разделе, посвященном панели команд. Цвета текста строки меню и панели команд рассматриваются в разделах, посвященных меню и панели команд.  
  
 ![Красная линия командной полки](../../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303 188_CommandShelfRedline")  
  
 Используйте:  
 -   для областей, где размещаются меню или панели инструментов;  
  
-   с правильным сочетанием имен токенов /? переднего.  
  
 Не используйте:  
 для областей, которые не похожи на командную полку.  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 Строка меню  
  
 Фон  
  
 *Ограничения градиента устанавливаются в одно и то же значение цвета в Visual Studio 2013 светлой и темной тем.*  
  
 `Environment.CommandShelfHighlightGradientBegin`  
  
 `Environment.CommandShelfHighlightGradientMiddle`  
  
 `Environment.CommandShelfHighlightGradientEnd`  
  
 Панель команд  
  
 Фон  
  
 *Ограничения градиента устанавливаются в одно и то же значение цвета в Visual Studio 2013 светлой и темной тем.*  
  
 `Environment.CommandShelfBackgroundGradientBegin`  
  
 `Environment.CommandShelfBackgroundGradientMiddle`  
  
 `Environment.CommandShelfBackgroundGradientEnd`  
  
## <a name="toolbox"></a>Панель элементов  
 Панель элементов — одно из стандартных окон инструментов, которое чаще всего используется в Visual Studio. По сути, это элемент управления типа "Дерево" с примененной к нему специальной темой и стилем.  
  
 ![Красная линия панели инструментов](../../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303 189_ToolboxRedline")  
  
 Используйте:  
 при разработке окна инструментов, которое всегда должно быть согласовано с панелью элементов оболочки.  
  
 Не используйте:  
 для компонентов, которые не похожи на панель элементов, или если вы опасаетесь, что могут возникнуть проблемы с вашим пользовательским интерфейсом при изменении цветов панели элементов оболочки.  
  
 **Default**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Родительский узел панели инструментов](../../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 190_ToolboxParentNode")  
  
 **Родительский узел**  
  
 ![Дочерний узел панели инструментов](../../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 191_ToolboxChildNode")  
  
 **Дочерний узел**  
  
 Фон  
  
 `Environment.ToolboxContent`  
  
 Заголовки  
  
 `Environment.ToolWindowBackground`  
  
 Отдельные элементы или все окно, если нет доступных элементов управления  
  
 Border  
  
 Нет  
  
 Передний план (глиф)  
  
 `Environment.ToolboxContent`  
  
 Передний план (текст)  
  
 `Environment.ToolboxContent`  
  
 **При наведении курсора мыши**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Дочерний узел панели инструментов при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")  
  
 **Панели инструментов при наведении на дочерний узел**  
  
 Фон  
  
 `Environment.ToolboxContentMouseOver`  
  
 Только отдельные элементы  
  
 Border  
  
 Нет  
  
 Передний план (текст)  
  
 `Environment.ToolboxContentMouseOver`  
  
 Только отдельные элементы  
  
 **Выбранные**  
  
 Компонент  
  
 Элемент  
  
 Имя токена: Category.color  
  
 ![Родительский узел панели инструментов с фокусом ввода](../../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")  
  
 **Фокус родительский узел**  
  
 ![Дочерний узел панели инструментов с фокусом ввода](../../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")  
  
 **Фокус дочерний узел**  
  
 Фон  
  
 `TreeView.SelectedItemActive`  
  
 Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)  
  
 Border  
  
 `TreeView.FocusVisualBorder`  
  
 Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)  
  
 Передний план (глиф)  
  
 `TreeView.SelectedItemActive`  
  
 Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)  
  
 Передний план (текст)  
  
 `TreeView.SelectedItemActive`  
  
 Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)  
  
 ![Родительский узел панели инструментов без фокуса ввода](../../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")  
  
 **Без фокуса ввода родительский узел**  
  
 ![Дочерний узел панели инструментов без фокуса ввода](../../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")  
  
 **Без фокуса ввода дочерний узел**  
  
 Фон  
  
 `TreeView.SelectedItemInactive`  
  
 Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)  
  
 Border  
  
 Нет  
  
 Передний план (глиф)  
  
 `TreeView.SelectedItemInactive`  
  
 Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)  
  
 Передний план (текст)  
  
 `TreeView.SelectedItemInactive`  
  
 Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

