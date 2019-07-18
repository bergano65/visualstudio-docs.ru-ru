---
title: Общие цвета для Visual Studio | Документация Майкрософт
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b36b7c123f4da9ca3ab7a6f33a972345cdf70e6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310781"
---
# <a name="shared-colors-for-visual-studio"></a>Общие цвета для Visual Studio
При разработке пользовательского интерфейса, который использует общие элементы оболочки Visual Studio, или вы хотите быть согласованы с аналогичными функциями элемента интерфейса, используйте существующие имена токенов в файлах определений пакетов для выбора и назначения цветов. Таким образом можно обеспечить согласованность пользовательского интерфейса со всей средой Visual Studio и его автоматическое обновление при добавлении или обновлении тем.

В этом разделе описываются стандартные элементы пользовательского интерфейса и используемые ими имена токенов, на которые можно ссылаться при разработке похожего пользовательского интерфейса. Более подробные сведения о доступе к этим токенам цветов см. в разделе [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Используйте имена токенов правильно.

- **Используйте имена токенов в соответствии с функцией, а не самим цветом.** Стандартные общие цвета связаны с определенными элементами интерфейса и предназначены для использования только для аналогичных или похожих функций. Например, не используйте цвет выбранного поля со списком для анимированного индикатора хода выполнения только потому, что вам понравился цвет. Функции поля со списком и анимации отличаются, и если цвет, связанный с изменениями поле со списком, он может больше не оказаться неподходящим для анимированного элемента. Согласованное использование цветов помогает пользователям ориентироваться в интерфейсе и предотвращает путаницу.

- **Используйте цвета фона и текста в правильном сочетании.** Цвет фона, предназначенный для текста, имеет соответствующий цвет текста. Не используйте цвета текста, отличные от тех, которые определены для данного цвета фона. Если не связан цвет текста, не используйте цвет фона для поверхности, на котором предполагается, что для отображения текста. Другие сочетания цветов текста и фона может привести к интерфейс неудобным для восприятия.

- **Используйте цвета элементов управления, соответствующие их расположению.** В определенных состояниях некоторые элементы управления Visual Studio нет отдельных границы и цвета фона. Эти цвета наследуются от областей, в которых они расположены. Всегда используйте имена токенов, которые подходят для того места, в котором вы размещаете элементы управления.

> [!IMPORTANT]
> Не используйте токены из категорий «Начальная страница» и «Cider».

## <a name="common-shared-controls"></a>Стандартные общие элементы управления

При использовании стандартной панели команд Visual Studio в компоненте, вы получите доступ к оформленным элементам управления оболочки. Не следует шаблон этих стандартных элементов управления. Однако если вам нужно создать пользовательскую панель команд, вам также может потребоваться создать пользовательские элементы управления. В этом случае используйте правильные имена токенов для каждого из указанных ниже элементов управления, чтобы ваш пользовательский интерфейс был согласован с остальной средой Visual Studio.

### <a name="button-controls"></a>Элементы управления "Кнопка"

![Красная линия управления "Кнопка"](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303 155_ButtonControlRedline")

| Используйте... | Не используйте... |
| --- | --- |
| … для кнопок в контейнере документа, которые нужно интегрировать с темами Visual Studio (Light, Темная, синяя или системная высококонтрастная тема). | … для кнопок, которые будут отображаться на пользовательском фоне, не являющимся частью темы Visual Studio. |

**Кнопки: стандартный состояние**

![Стандартной кнопки](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Стандартной кнопки

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Кнопка | `CommonControls.Button` |
| Граница кнопки | `CommonControls.ButtonBorder` |

**Кнопки: состояние по умолчанию**

![Кнопка по умолчанию](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Кнопка по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Кнопка | `CommonControls.ButtonDefault` |
| Граница кнопки | `CommonControls.ButtonBorderDefault` |

**Кнопка: отключена**

![Кнопку в отключенном состоянии](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Кнопку в отключенном состоянии

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Кнопка | `CommonControls.ButtonDisabled` |
| Граница кнопки | `CommonControls.ButtonBorderDisabled` |

**Кнопки: состояние при наведении указателя мыши**

![Кнопка при наведении курсора мыши](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Кнопка при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Кнопка | `CommonControls.ButtonHover` |
| Граница кнопки | `CommonControls.ButtonBorderHover` |

**Кнопка: нажата**

![Кнопку в нажатом состоянии](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Кнопку в нажатом состоянии

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Кнопка | `CommonControls.ButtonPressed` |
| Граница кнопки | `CommonControls.ButtonBorderPressed` |

**Кнопка: состояние с фокусом ввода**

![Кнопка с фокусом ввода](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Кнопка с фокусом ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Кнопка | `CommonControls.ButtonFocused` |
| Граница кнопки | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Элементы управления "Флажок"
![Флажок (красная линия)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303 161_CheckboxRedline")<br />Флажок (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … для элементов управления "флажок", содержащихся в документе, хорошо. | … для пользовательского интерфейса, который не элемент управления "флажок". |

**Флажок: состояние по умолчанию**

![Флажок](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303 162_Checkbox")<br />По умолчанию флажок

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `CommonControls.CheckBoxBackground` |
| Border | `CommonControls.CheckBoxBorder` |
| Текста | `CommonControls.CheckBoxText` |
| Глиф | `CommonControls.CheckBoxGlyph` |

**Флажок: отключенном состоянии**

![Отключенный флажок](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303 163_CheckboxDisabled")<br />Отключенный флажок

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `CommonControls.CheckBoxBackgroundDisabled` |
| Border | `CommonControls.CheckBoxBorderDisabled` |
| Текста | `CommonControls.CheckBoxTextDisabled` |
| Глиф | `CommonControls.CheckBoxGlyphDisabled` |

**Флажок: наведите указатель мыши на состояния**

 ![Флажок при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303 164_CheckboxHover")<br />Флажок при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `CommonControls.CheckBoxBackgroundHover` |
| Border | `CommonControls.CheckBoxBorderHover` |
| Текста | `CommonControls.CheckBoxTextHover` |
| Глиф | `CommonControls.CheckBoxGlyphHover` |

**Флажок: нажат**

![Нажатый флажок](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303 165_CheckboxPressed")<br />Нажатый флажок

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `CommonControls.CheckBoxBackgroundPressed` |
| Border | `CommonControls.CheckBoxBorderPressed` |
| Текста | `CommonControls.CheckBoxTextPressed` |
| Глиф | `CommonControls.CheckBoxGlyphPressed` |

**Флажок: состояние с фокусом ввода**

![Фокус флажок](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303 166_CheckboxFocused")<br />Фокус флажок

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `CommonControls.CheckBoxBackgroundFocused` |
| Border | `CommonControls.CheckBoxBorderFocused` |
| Текста | `CommonControls.CheckBoxTextFocused` |
| Глиф | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Раскрывающийся список и поля со списком полей
![Раскрывающийся список/со списком (красная линия)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303 167_DropDownComboBoxRedline")<br />Раскрывающийся список/со списком (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … для раскрывающемся списке и поле со списком полей в документе также. | … для пользовательского интерфейса, которые не находятся в поле раскрывающегося списка или поля со списком. |
| | … для панели команд [раскрывающиеся меню](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) или [списком](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Раскрывающийся список и поля со списком полей: состояние по умолчанию**

![По умолчанию раскрывающийся список/списком](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303 168_DropDownComboBox")<br />По умолчанию раскрывающийся список/со списком

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `CommonControls.ComboBoxBackground` |
| Border | `CommonControls.ComboBoxBorder` |
| Текста | `CommonControls.ComboBoxText` |
| Separator | `CommonControls.ComboBoxSeparator` |
| Глиф | `CommonControls.ComboBoxGlyph` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackground` |

**Раскрывающийся список и поля со списком полей: отключенном состоянии**

![Отключенные раскрывающийся список/списком](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")<br />Отключенные раскрывающийся список/со списком

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `CommonControls.ComboBoxBackgroundDisabled` |
| Border | `CommonControls.ComboBoxBorderDisabled` |
| Текста | `CommonControls.ComboBoxTextDisabled` |
| Separator | `CommonControls.ComboBoxSeparatorDisabled` |
| Глиф | `CommonControls.ComboBoxGlyphDisabled` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Раскрывающийся список и поля со списком полей: наведите указатель мыши на состояния**

![Раскрывающийся список/со списком при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")<br />Раскрывающийся список/поле со списком при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `CommonControls.ComboBoxBackgroundHover` |
| Border | `CommonControls.ComboBoxBorderHover` |
| Текста | `CommonControls.ComboBoxTextHover` |
| Separator | `CommonControls.ComboBoxSeparatorHover` |
| Глиф | `CommonControls.ComboBoxGlyphHover` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Раскрывающийся список и поля со списком полей: нажат**

![Нажата раскрывающийся список/списком](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")<br />Нажата раскрывающийся список/со списком

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `CommonControls.ComboBoxBackgroundPressed` |
| Border | `CommonControls.ComboBoxBorderPressed` |
| Текста | `CommonControls.ComboBoxTextPressed` |
| Separator | `CommonControls.ComboBoxSeparatorPressed` |
| Глиф | `CommonControls.ComboBoxGlyphPressed` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Раскрывающийся список и поля со списком полей представление элементов списка: нажат**

 ![Раскрывающийся список/списком нажатии элемента представления списка](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")<br />Раскрывающийся список/списком нажатии элемента представления списка

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Border | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Текст элемента | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Фон с тенью | `CommonControls.ComboBoxListBackgroundShadow` |

**Раскрывающийся список и поля со списком полей: состояние с фокусом ввода**

![Раскрывающийся список/со списком с фокусом](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")<br />Раскрывающийся список/со списком с фокусом

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `CommonControls.ComboBoxBackgroundFocused` |
| Border | `CommonControls.ComboBoxBorderFocused` |
| Текста | `CommonControls.ComboBoxTextFocused` |
| Separator | `CommonControls.ComboBoxSeparatorFocused` |
| Глиф | `CommonControls.ComboBoxGlyphFocused` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Раскрывающийся список и поля со списком полей: Выбор ввода текста**

![Выбор раскрывающегося списка/со списком ввода](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303 173_DropDownComboBoxTextInput")<br />Выбор раскрывающегося списка/со списком ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Выделение | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Табличные элементы управления данными (сетка)
Табличные элементы управления данными, также называемые элементами управления "Сетка", — это стандартные элементы управления Visual Studio, которые можно использовать для представления больших объемов данных в нескольких столбцах. Стандартные табличные элементы управления данными встречаются в Visual Studio в нескольких местах: в окне инструментов "Список ошибок", в отчетах IntelliTrace, в представлении кучи памяти и т. д. Всегда используйте стандартные табличные элементы управления данными. Однако в некоторых редких случаях доступ к стандартным табличным элементам управления данными может отсутствовать. В таких ситуациях используйте указанные ниже имена токенов для обеспечения согласованности пользовательского интерфейса с другими табличными элементами управления данными в Visual Studio.

![Элемент управления сетки и табличных данных (красная линия)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")<br />Элемент управления сетки и табличных данных (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … для табличной или элементами управления DataGrid. | … для пользовательского интерфейса, который не является элементом управления табличных или сетки. |

#### <a name="column-headers"></a>Заголовки столбцов
Заголовки столбцов состоят из фона, границы, текста заголовка и необязательного глифа, который обычно используется при сортировке сетки по данному столбцу.

**Заголовок столбца: состояние по умолчанию**

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Header.Default` |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Header.Glyph` |
| Border | `Header.SeparatorLine` |

**Заголовок столбца: наведите указатель мыши на состояния**

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Header.MouseOver` |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Передний план (глиф) | `Header.MouseOverGlyph` |
| Border | `Header.SeparatorLine` |

**Заголовок столбца: нажат**

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `CommonControls.CheckBoxBackgroundPressed` |
| Передний план (текст) | `CommonControls.CheckBoxBorderPressed` |
| Передний план (глиф) | `CommonControls.CheckBoxTextPressed` |
| Border | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Элементы представления списка
 Элементы представления списка состоят из фона и содержимого. Содержимым может быть текст, значок или и то и другое.

**Элементы представления списка: состояние по умолчанию**

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Прозрачный |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Border | Нет |

**Элементы представления списка: активное состояние**

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `TreeView.SelectedItemActive` |
| Передний план (текст) | `TreeView.SelectedItemActiveText` |
| Border | Нет |

**Элементы представления списка: неактивное состояние**

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `TreeView.SelectedItemInactive` |
| Передний план (текст) | `TreeView.SelectedItemInactiveText` |
| Border | Нет |

### <a name="ui-text"></a>Текст пользовательского интерфейса

#### <a name="instructional-text"></a>Пояснительный текст
Пояснительный текст дает важных основных объяснение того, что следует сделать на странице диалогового окна или документа.

![Пояснительный текст по умолчанию](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Пояснительный текст по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Дополнительный текст инструкции
На страницах документа с большим количеством текста и элементов управления пояснительный текст используется значение другим цветом. Это помогает передачи, какая информация является наиболее важным, а также снижать общая плотность элементы пользовательского интерфейса. (Также см. в разделе под разделом на текст подсказки.)

![Дополнительный текст инструкции](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Дополнительный текст инструкции

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Текст подсказки
Текст подсказки отображается в пустой элемент управления, под элемент управления или в рабочей области пустой документ для представления пользователю, что делать дальше. Пояснительный текст можно использовать с фоном окна или элемента управления.

**Текст подсказки по умолчанию**

![По умолчанию текст подсказки](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Текст подсказки по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `Environment.ControlEditHintText` |

**Требуется пояснительный текст**

![Необходимый текст подсказки](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Требуется пояснительный текст

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `Environment.ControlRequiredHintText` |
| Фон | `Environment.ControlRequiredBackground` |

**Текст элемента управления в поле поиска**

> См. в разделе [окна поиска](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) для других токены цветов, связанных с элементом управления поиска.

![Search box control text](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Текст элемента управления в поле поиска

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Гиперссылка
Гиперссылка представляет один элемент управления, который не содержит пару переднего плана и фона. Во всех случаях используйте основной цвет гиперссылки, который будет правильно отображаться на темном, сером и белым фоном. Если вы не используете токен цвета для элемента управления hyperlink, вы увидите, что по умолчанию системный цвет для «pressed», который будет мигать красным. Это означает, что элемент управления не использует неправильный токен цвета среды.

![Гиперссылка (красная линия)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303 133_HyperlinkRedline")<br />Гиперссылка (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| ... Если вам нужно создать пользовательскую гиперссылку. | … для параметров, которые не гиперссылки. |

**Гиперссылки: состояние по умолчанию**

![Гиперссылка по умолчанию](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303 134_Hyperlink")<br />Гиперссылка по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlink` |

**Гиперссылки: состояние наведения**

![Гиперссылка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303 135_HyperlinkHover")<br />Гиперссылка при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlinkHover` |

**Гиперссылки: нажатом состоянии**

![Нажатой гиперссылки](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303 136_HyperlinkPressed")<br />Гиперссылки в нажатом состоянии

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlinkPressed` |

**Гиперссылки: отключена**

![Отключенные hyperlink](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303 137_HyperlinkDisabled")<br />Отключенные гиперссылки

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Информационные панели
Информационные панели служат для предоставления дополнительной информации о данном контексте и всегда отображаются в верхней части окна документа или окна инструментов.

![Информационная панель (красная линия)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303 138_InfobarRedline")<br />Информационная панель (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … При создании пользовательских информационных панелей. | … для элементов пользовательского интерфейса, которые не похожи на информационную панель. |

**Информационной панели: состояние по умолчанию**

![По умолчанию информационная панель](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303 139_Infobar")<br />Информационная панель по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `InfoBar.InfoBarBackground` |
| Передний план (текст) | `InfoBar.InfoBar` |
| Border | `InfoBar.InfoBarBorder` |

**Закрыть панель сведений (&times;) кнопки: состояние по умолчанию**

![По умолчанию закрыть информационную панель (&times;) кнопку](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />По умолчанию закрыть информационную панель (&times;) кнопку

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `InfoBar.CloseButton` |
| Border | `InfoBar.CloseButtonBorder` |
| Глиф | `InfoBar.CloseButtonGlyph` |

**Закрыть панель сведений (&times;) кнопки: наведите указатель мыши на состояния**

![Закрыть панель сведений (&times;) кнопка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Закрыть панель сведений (&times;) кнопка при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `InfoBar.CloseButtonHover` |
| Border | `InfoBar.CloseButtonHoverBorder` |
| Глиф | `InfoBar.CloseButtonHoverGlyph` |

**Закрыть панель сведений (&times;) кнопки: нажат**

![Нажата закрыть информационную панель (&times;) кнопку](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Нажата закрыть информационную панель (&times;) кнопку

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `InfoBar.CloseButtonDown` |
| Border | `InfoBar.CloseButtonDownBorder` |
| Глиф | `InfoBar.CloseButtonDownGlyph` |

**Информационная панель кнопку гиперссылки: состояние по умолчанию**

![Кнопку гиперссылки информационная панель по умолчанию](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Кнопку гиперссылки информационная панель по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `InfoBar.Hyperlink` |

**Информационная панель кнопку гиперссылки: наведите указатель мыши на состояния**

![Кнопку гиперссылки информационной панели при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Кнопку гиперссылки информационной панели при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseOver`<br />(С подчеркиванием) |

**Информационная панель кнопку гиперссылки: нажат**

![Нажата информационной панели кнопку гиперссылки](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Кнопку гиперссылки нажатом информационной панели

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseDown`<br />(С подчеркиванием) |

**Hyperlink встроенный информационной панели (в предложении): состояние по умолчанию**

![Информационная панель гиперссылки по умолчанию встроенной кнопки](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Информационная панель гиперссылки по умолчанию встроенной кнопки

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `InfoBar.Hyperlink` |

**Hyperlink встроенный информационной панели (в предложении): при наведении указателя мыши на состояния**

![Встроенной кнопки гиперссылки на информационной панели при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Встроенной кнопки гиперссылки на информационной панели при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseOver`<br />(С подчеркиванием) |

**Hyperlink встроенный информационной панели (в предложении): нажат**

![Кнопку гиперссылки встроенный нажатом информационная панель](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Активная кнопка hyperlink встроенный информационной панели

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseDown`<br />(С подчеркиванием) |

**Кнопка информационная панель: состояние по умолчанию**

![Кнопка информационная панель по умолчанию](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Кнопка по умолчанию информационной панели

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `InfoBar.Button` |
| Передний план (текст) | `InfoBar.Button` |
| Border | `InfoBar.ButtonBorder` |

**Кнопка информационная панель: наведите указатель мыши на состояния**

![Информационная панель Кнопка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Информационная панель Кнопка при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `InfoBar.ButtonMouseOver` |
| Передний план (текст) | `InfoBar.ButtonMouseOver` |
| Border | `InfoBar.ButtonMouseOverBorder` |

**Кнопка информационная панель: нажат**

![Кнопка нажата информационная панель](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Кнопка нажата информационной панели

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `InfoBar.ButtonMouseDown` |
| Передний план (текст) | `InfoBar.ButtonMouseDown` |
| Border | `InfoBar.ButtonMouseDownBorder` |

**Кнопка информационная панель: отключенном состоянии**

![Отключенные информационной панели кнопку](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Отключенные информационная панель кнопку

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `InfoBar.ButtonDisabled` |
| Передний план (текст) | `InfoBar.ButtonDisabled` |
| Border | `InfoBar.ButtonDisabledBorder` |

**Кнопка информационная панель: состояние с фокусом ввода**

![Кнопка с фокусом информационная панель](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Кнопка с фокусом информационной панели

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `InfoBar.ButtonFocus` |
| Передний план (текст) | `InfoBar.ButtonFocus` |
| Border | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Полосы прокрутки
Полосы прокрутки выглядят средой Visual Studio и не должны быть оформлены стилистически. Тем не менее вы решите, что вы хотите использовать цвета, применяемые в полосах прокрутки, чтобы пользовательский Интерфейс был согласован с этой частью среды Visual Studio.

![Полосы прокрутки (красная линия)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303 140_ScrollbarRedline")<br />Полосы прокрутки (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … При создании пользовательского интерфейса, необходимо в соответствии с Visual Studio полосы прокрутки. | ... сведения обо всех проблемах, вы не должны всегда соответствовать прокрутите панель пользовательского интерфейса. |

**Полоса прокрутки: состояние по умолчанию**

![Полоса прокрутки по умолчанию](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303 141_Scrollbar")<br />Полоса прокрутки по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Полоса прокрутки | `Environment.ScrollBarBackground` |
| Передний план (бегунок) | `Environment.ScrollBarThumbBackground` |

**Полоса прокрутки: наведите указатель мыши на состояния**

![Полосы прокрутки при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303 143_ScrollbarHover")<br />Полоса прокрутки при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Полоса прокрутки | `Environment.ScrollBarBackground` |
| Передний план (бегунок) | `Environment.ScrollBarThumbMouseOverBackground` |

*Полоса прокрутки: нажат**

![Полосы прокрутки в нажатом состоянии](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303 145_ScrollbarPressed")<br />Нажата полосы прокрутки

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Полоса прокрутки | `Environment.ScrollBarBackground` |
| Передний план (бегунок) | `Environment.ScrollBarThumbPressedBackground` |

**Полоса стрелку прокрутки: состояние по умолчанию**

![Стрелки полосы прокрутки по умолчанию](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303 142_ScrollbarArrow")<br />Стрелки полосы прокрутки по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ScrollBarArrowBackground`<br />(Значение совпадает с цветом полосы прокрутки). |
| Передний план (глиф) | `Environment.ScrollBarArrowGlyph` |

**Полоса стрелку прокрутки: наведите указатель мыши на состояния**

![Прокрутите панель со стрелками при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303 144_ScrollbarArrowHover")<br />Стрелки полосы прокрутки при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ScrollBarArrowMouseOverBackground`<br />(Значение совпадает с цветом полосы прокрутки). |
| Передний план (глиф) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Полоса стрелку прокрутки: нажат**

![Стрелки полосы прокрутки в нажатом состоянии](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")<br />При нажатии стрелки полосы прокрутки

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ScrollBarArrowPressedBackground`<br />(Значение совпадает с цветом полосы прокрутки). |
| Передний план (глиф) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="BKMK_SearchBoxes"></a>Поля поиска
По возможности используйте стандартный элемент управления поиском, предоставляемый средой Visual Studio. Цвета поля поиска находятся в категории SearchControl в файле **ShellColors.pkgdef** , который содержит имена токенов для поля ввода, управляющей кнопки, кнопки раскрывающегося списка и раскрывающегося меню.

Поле поиска может находиться в одном из нескольких состояний. Некоторые из них взаимоисключающие.

- "С фокусом ввода" или "без фокуса ввода" указывает на то, находится ли курсор в текстовом поле.

- "Активно" или "неактивно" указывает на то, ввел ли пользователь запрос в текстовом поле.

- "При наведении указателя" означает, что пользователь навел указатель мыши на поле поиска (это состояние переопределяет все остальные).

- "Отключено" означает, что функция поиска в текущем контексте отключена.

![Поле поиска (красная линия)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303 110_SearchBoxRedline")<br />Поле поиска (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … При разработке пользовательского поля поиска. | ... сведения обо всех проблемах, которые не находятся в поле поиска. |
| | … для параметров, которые вы не должны всегда соответствовать поиск поле пользовательского интерфейса. |

**Поле ввода окна поиска с фокусом ввода**

![Поле ввода для направленного поиска](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br />Поле ввода окна поиска с фокусом ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `SearchControl.FocusedBackground` |
| Передний план (текст) | `SearchControl.FocusedBackground` |
| Border | `SearchControl.FocusedBorder` |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Поле ввода окна поиска без фокуса ввода, активный**

![Поле ввода окна поиска без фокуса ввода](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br />Поле ввода окна поиска без фокуса ввода, активный

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `SearchControl.SearchActiveBackground` |
| Передний план (текст) | `SearchControl.SearchActiveBackground` |
| Border | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Поле ввода окна поиска без фокуса ввода, неактивные**

![Поле ввода окна поиска без фокуса ввода, неактивные](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Поле ввода окна поиска без фокуса ввода, неактивные

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `SearchControl.Unfocused` |
| Передний план (текст) | `SearchControl.Unfocused` |
| Border | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Поле ввода окна поиска выделенный (текст)**

![Поле ввода окна поиска выделенный](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br />Поле ввода окна поиска выделенные

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `SearchControl.Selection` |
| Передний план (текст) | `SearchControl.FocusedBackground` |
| Border | Нет |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Поле ввода окна поиска отключено**

![Disabled search input field](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Поле ввода окна поиска отключено

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `SearchControl.Disabled` |
| Передний план (текст) | `SearchControl.Disabled` |
| Border | `SearchControl.DisabledBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Кнопка поиска с фокусом ввода**

![Кнопка поиска с фокусом ввода](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br />Кнопка поиска с фокусом ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Нет |
| Передний план (глиф поиска) | `SearchControl.SearchGlyph` |
| Передний план (глиф остановки) | `SearchControl.StopGlyph` |
| Передний план (глиф очистки) | `SearchControl.ClearGlyph` |
| Border | Н/Д |

**Кнопка поиска без фокуса ввода**

![Кнопка поиска без фокуса ввода](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br />Кнопка поиска без фокуса ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Н/Д |
| Передний план (глиф поиска) | `SearchControl.SearchGlyph` |
| Передний план (глиф остановки) | `SearchControl.StopGlyph` |
| Передний план (глиф очистки) | `SearchControl.ClearGlyph` |
| Border | Н/Д |

**Нажата кнопка поиска**

![Кнопка нажата поиска](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Нажата кнопка поиска

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `SearchControl.ActionButtonMouseDown` |
| Передний план (глиф) | `SearchControl.ActionButtonMouseDownGlyph` |
| Border | `SearchControl.ActionButtonMouseDownBorder` |

**Кнопка поиска отключено**

![Неактивная кнопка поиска](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")<br />Кнопка поиска отключено

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Нет |
| Передний план (глиф) | `SearchControl.ActionButtonDisabledGlyph` |
| Border | Нет |

**Кнопка раскрывающегося списка для направленного поиска**

![Кнопка раскрывающегося списка для направленного поиска](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")<br />Кнопка раскрывающегося списка для направленного поиска

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `SearchControl.FocusedDropDownButton` |
| Передний план (глиф) | `SearchControl.FocusedDropDownButtonGlyph` |
| Border | `SearchControl.FocusedDropDownButtonBorder` |

**Кнопка раскрывающегося списка поиска без фокуса ввода**

![Кнопка раскрывающегося списка поиска без фокуса ввода](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")<br />Кнопка раскрывающегося списка поиска без фокуса ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `SearchControl.UnfocusedDropDownButton` |
| Передний план (глиф) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Border | `SearchControl.UnfocusedDropDownButtonBorder` |

**Активная кнопка раскрывающегося списка поиска**

![Кнопка раскрывающегося списка поиска нажатом](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Активная кнопка раскрывающегося списка поиска

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `SearchControl.MouseDownDropDownButton` |
| Передний план (глиф) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Border | `SearchControl.MouseDownDropDownButtonBorder` |

**Кнопка раскрывающегося списка поиска отключено**

![Кнопка раскрывающегося списка поиска отключено](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")<br />Кнопка раскрывающегося списка поиска отключено

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Нет |
| Передний план (глиф) | `SearchControl.DisabledDownButtonGlyph` |
| Border | Нет |

#### <a name="search-drop-down-lists"></a>Раскрывающиеся списки поиска
Выберите в раскрывающемся меню поля поиска может быть немного сложнее, чем другие раскрывающиеся меню в Visual Studio. «Предлагаемые запросы поиска» и «параметры поиска» разделы могут использоваться отдельно или вместе в меню, и окрашивается каждый из них отдельно. Если имеются оба этих раздела, они разделяются линией, а все раскрывающееся меню окружено границей.

![Стрелку раскрывающегося списка поиска (красная линия)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303 124_SearchDropdownRedline")<br />Стрелку раскрывающегося списка поиска (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … При создании пользовательского раскрывающегося списка поиска. | … Для раскрывающихся списков, которые отображаются в других контекстах. |
| … правильные имена токенов для соответствующих компонентов списка. | ... в любые кроме указанного сочетания фона и цвета переднего плана. |

**Элементы раскрывающегося списка поиска**

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Border | `SearchControl.PopupBorder` |
| Separator | `SearchControl.PopupSectionHeaderSeparator` |
| Тень | `Environment.DropShadowBackground` |

**Рекомендуемые поисковые запросы: состояние по умолчанию**

![По умолчанию предлагаемые запросы поиска](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303 125_SearchSuggested")<br />По умолчанию предлагаемые запросы поиска

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `SearchControl.PopupItemText` |

**Рекомендуемые поисковые запросы: наведите указатель мыши на состояния**

![Рекомендуемые поисковые запросы, при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303 128_SearchSuggestedHover")<br />Предлагаемые запросы поиска при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `SearchControl.PopupMouseOverItemText` |
| Border | `SearchControl.PopupControlMouseOverBorder` |

**Параметры поиска: состояние по умолчанию**

![Флажок поиска](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303 126_SearchCheckbox")<br />По умолчанию параметры поиска (флажок)

![Параметры поиска](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303 127_SearchOptions")<br />Параметры поиска по умолчанию (ссылка)

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст флажка) | `SearchControl.PopupCheckboxText` |
| Передний план (текст ссылки) | `SearchControl.PopupButtonText` |
| Фон заголовка | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст заголовка) | `SearchControl.PopupSectionHeaderText` |

**Параметры поиска: наведите указатель мыши на состояния**

![Параметры (флажок) поиска при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br />Параметры поиска (флажок) при наведении курсора мыши

![Параметры (ссылка) поиска при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303 130_SearchOptionsHover")<br />Параметры поиска (ссылка) при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст флажка) | `SearchControl.PopupCheckboxMouseDownText` |
| Передний план (текст ссылки) | `SearchControl.PopupButtonMouseDownText` |
| Border | `SearchControl.PopupControlMouseOverBorder` |

**Параметры поиска: нажат**

![Нажата параметры поиска (флажок)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br />Нажата параметры поиска (флажок)

![Нажата параметры поиска (ссылка)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303 132_SearchOptionsPressed")<br />Нажата параметры поиска (ссылка)

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон флажка | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст флажка) | `SearchControl.PopupCheckboxMouseDownText` |
| Фон ссылки | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст ссылки) | `SearchControl.PopupButtonMouseDownText` |

### <a name="BKMK_TreeView"></a> Представления в виде дерева
Несколько окон инструментов, включая обозреватель решений, обозреватель серверов и представление классов, реализовать иерархическая организационная схема, цвета определяются названиями цветов в `TreeView` категории. Все элементы в иерархическом представлении имеют цвета фона и текста. Элементы с вложенными дочерними элементами также имеют глифы, которые указывают на то, является ли элемент свернутым или развернутым.

![Представление в виде дерева (красная линия)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303 147_TreeViewRedline")<br />Представление в виде дерева (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … в любом необходимо реализовать иерархическое представление. | … для параметров, которые не аналогично представлению в виде дерева. |
| | ... в любые кроме указанного сочетания фона и цвета переднего плана. |

**Элемент дерева: состояние по умолчанию**

![По умолчанию элемент дерева](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303 148_TreeView")<br />По умолчанию элемент дерева

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `TreeView.Background` |
| Передний план (текст) | `TreeView.Background` |
| Передний план (глиф) | `TreeView.Glyph` |
| Border | Нет |

**Элемент дерева: наведите указатель мыши на состояния**

![Элемент дерева при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303 149_TreeViewHover")<br />Элемент дерева при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `TreeView.Background` |
| Передний план (текст) | `TreeView.Background` |
| Передний план (глиф) | `TreeView.GlyphMouseOver` |
| Border | Нет |

**Элемент дерева: перетащите на состояние**

![Древовидная элемент представления на перетаскивания над](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303 150_TreeViewDragOver")<br />Перетащите элемент дерева на

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `TreeView.DragOverItem` |
| Передний план (текст) | `TreeView.DragOverItem` |
| Передний план (глиф) | `TreeView.DragOverItemGlyph` |
| Border | Нет |

**Элемент дерева: выбран, то состояние с фокусом ввода**

![Выбран и с фокусом ввода элемента представления дерева](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303 151_TreeViewFocused")<br />Элемент дерева выбранного и находящиеся в фокусе

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `TreeView.SelectedItemActive` |
| Передний план (текст) | `TreeView.SelectedItemActive` |
| Передний план (глиф) | `TreeView.SelectedItemActiveGlyph` |
| Border | `TreeView.FocusVisualBorder` |

**Элемент дерева: состояние выбранного, без фокуса ввода**

![Элемент дерева выбранного и без фокуса ввода](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303 152_TreeViewUnfocused")<br />Элемент дерева выбранного и без фокуса ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `TreeView.SelectedItemInactive` |
| Передний план (текст) | `TreeView.SelectedItemInactive` |
| Передний план (глиф) | `TreeView.SelectedItemInactiveGlyph` |
| Border | Нет |

**Элемент дерева: указателем мыши, установлен и состояние с фокусом ввода**

![Выбран и элемент дерева с фокусом ввода при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br />Элемент дерева выбранного и находящиеся в фокусе при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `TreeView.SelectedItemActive` |
| Передний план (текст) | `TreeView.SelectedItemActive` |
| Передний план (глиф) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Border | `TreeView.FocusVisualBorder` |

**Элемент дерева: состояние при наведении указателя мыши, выбранный и без фокуса ввода**

![Элемент дерева выбранного и без фокуса ввода при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br />Элемент дерева выбранного и без фокуса ввода при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `TreeView.SelectedItemInactive` |
| Передний план (текст) | `TreeView.SelectedItemInactive` |
| Передний план (глиф) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Border | Нет |

## <a name="shell-appearance"></a>Внешний вид оболочки

### <a name="background"></a>Фон
Фон среды состоит из двух слоев. Нижний слой представляет собой сплошной цвет, который охватывает всю интегрированную среду разработки. Верхний слой используется под командной полкой и между каналами автоматического скрытия окон инструментов по левому и правому краям интегрированной среды разработки. Слои фона верхней и нижней частях устанавливаются в светлой и темной тем же цветом.

![Фон оболочки Visual Studio (красная линия)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303 187_ShellBackgroundRedline")<br />Фон оболочки Visual Studio (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … для места, где необходимо соответствовать фону среды Visual Studio. | … как заливки для областей, которые не являются фоновыми. |
| | … как фон размещаться элементы переднего плана на. |

**Вид оболочки нижнего уровня**

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.EnvironmentBackground` |

**Вид оболочки верхний слой**

> Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Командная полка
Для фона командной полки используются два набора имен токенов: один для области размещения строки меню, а другой — для области размещения панелей команд. Отдельные группы на панели команд имеют собственные значения цветов фона, которые более подробно рассматриваются в разделе, посвященном панели команд. Цвета текста строки меню и панели команд рассматриваются в разделах, посвященных меню и панели команд.

![Visual Studio командная Полка (красная линия)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303 188_CommandShelfRedline")<br />Visual Studio командная Полка (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| ... для областей, где размещаются меню или панели инструментов. | ... для областей, которые не аналогичную полки команд. |
|… с сочетанием имя токена правильный фона и цвета переднего плана. | |

**Строка меню командной полки**

> Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Панель команд командной полки**

> Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Конструктор манифеста
Конструктор манифеста призван упростить редактирование файла манифеста в проектах Windows 8 и Windows Phone 8. Хотя общего готового шаблона нет, рекомендуется обеспечивать соответствие макету и цветам вкладок ориентации и навигации, а также общей структуре. Дополнительные сведения о макете см. в разделе [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Конструктор манифеста (красная линия)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303 175_ManifestDesignerRedline")<br />Конструктор манифеста (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … для конструкторов, которые похожи на конструктор манифеста. | … При наличии более чем шести вкладок. |
| … Вместо использования стандартных элементов управления вкладки в верхней части редактора в контейнере документа хорошо. | … для пользовательского интерфейса, не структурированных от конструктора манифеста. |

**Вкладка "манифест конструктор выбранного": состояние по умолчанию**

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `ManifestDesigner.TabActive` |
| Border | Нет |

**Манифеста панель конструктора выбранного описания: состояние по умолчанию**

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `ManifestDesigner.DescriptionPane` |

**Страница выбранного содержимого манифеста конструктора: состояние по умолчанию**

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `ManifestDesigner.Background` |
| Текст подсказки для диалогового окна | `ManifestDesigner.WatermarkText`<br />(Это имя токена не соответствует его функции.) |

**Вкладка "манифест конструктор": невыделенного состояния**

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `ManifestDesigner.Tab.Inactive` |

**Вкладка "манифест конструктор": при наведении указателя мыши на состояния**

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Структура команд

### <a name="BKMK_CommandMenus"></a> Меню
Меню могут происходить в нескольких местах в Visual Studio: в строке главного меню, внедренные в документ или инструмент windows или правой кнопкой мыши таблицу, в разных местах внутри интегрированной среды разработки. Реализация меню, связанных с другими элементами пользовательского интерфейса, рассматривается в разделах, посвященных соответствующим элементам. Всегда используйте стандартную реализацию меню, предоставляемую средой Visual Studio. Однако в некоторых редких случаях доступ к стандартным меню Visual Studio может отсутствовать. В таких ситуациях используйте указанные ниже имена токенов для обеспечения согласованности пользовательского интерфейса с другими меню в Visual Studio.

![Меню Visual Studio (красная линия)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303 000_MenuRedline")<br />Меню Visual Studio (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| ... Если вам нужно создать пользовательское меню.| … только цветом фона. Всегда используйте определенное сочетание цвета фона и цвета переднего плана. |
| ... Если у вас есть новый компонент пользовательского интерфейса, которые должны соответствовать меню Visual Studio.| |

#### <a name="menu-titles"></a>Меню заголовков
Заголовок меню состоит из фона, границы и текста заголовка, а также необязательного глифа (обычно если меню находится на панели команд).

![Заголовок меню (красная линия)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303 001_MenuTitleRedline")<br />Заголовок меню (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … Каждый раз, когда вы создаете пользовательского заголовка меню. | … для параметров, которые вы не хотите всегда соответствовать заголовку меню. |
| | ... в любые кроме указанного сочетания фона и цвета переднего плана. |

**Заголовок меню: состояние по умолчанию**

![По умолчанию заголовок меню](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303 002_MenuTitleDefault")<br />Заголовок меню по умолчанию

![По умолчанию заголовок меню с глифом](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")<br />По умолчанию заголовок меню с глифом

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Нет |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Environment.CommandBarMenuGlyph` |
| Border | Нет |

**Заголовок меню: наведите указатель мыши на состояния**

![Заголовок меню при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303 004_MenuTitleHover")<br />Заголовок меню при наведении курсора мыши

![Заголовок меню с глифом при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")<br />Заголовок меню с глифом при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Передний план (глиф) | `Environment.CommandBarMenuMouseOverGlyph` |
| Border | `Environment.CommandBarBorder` |

**Заголовок меню: нажат**

![Заголовок меню нажата](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303 006_MenuTitlePressed")<br />Заголовок меню в нажатом состоянии

![Нажатие заголовка меню с глифом](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")<br />Нажатие заголовка меню с глифом

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Environment.CommandBarMenuMouseDownGlyph` |
| Border | `Environment.CommandBarMenuBorder`<br />(Только левую, верхнюю и правую части.) |

**Заголовок меню: отключенном состоянии**

![Отключить заголовок меню с глифом](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br />Заголовок отключенного меню с глифом

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Нет |
| Передний план (текст) | `Environment.CommandBarTextInactive` |
| Передний план (глиф) | `Environment.CommandBarTextInactive` |
| Border | Нет |

#### <a name="menu-items"></a>Пункты меню
Отдельный пункт меню состоит из текста и необязательных значка, флажка или глифа подменю. Его цвета фона и текста меняются при наведении указателя. Этот токен цвета представляет собой пару, состоящую из цвета фона и цвета переднего плана.

![Красная линия пунктов меню](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303 009_MenuItemRedline")

| Используйте... | Не используйте... |
|---|---|
| … для любого раскрывающегося списка, запускаемый из строки меню или панели команд. | … для раскрывающегося списка в другом контексте. |
| | ... в любые кроме указанного сочетания фона и цвета переднего плана. |

**Пункты меню: состояние по умолчанию**

![По умолчанию элементы меню](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303 010_MenuDefault")<br />Элементы меню по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф подменю) | `Environment.CommandBarMenuSubmenuGlyph` |
| Border | `Environment.CommandBarMenuBorder` |
| Фон канала значка | `Environment.CommandBarMenuIconBackground` |
| Separator | `Environment.CommandBarMenuSeparator` |
| Тень | `Environment.DropShadowBackground` |

**Пункты меню: флажок установлен и выбранные состояния**

![Меню с установленным флажком](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303 011_MenuChecked")<br />Checked меню

![Выбранное меню](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303 012_MenuSelected")<br />Выбранного пункта меню

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Флажок | `Environment.CommandBarCheckBox` |
| Фон флажка | `Environment.CommandBarSelectedIcon` |
| Фон значка | `Environment.CommandBarSelected` |
| Граница значка | `Environment.CommandBarSelectedBorder` |

**Пункты меню: наведите указатель мыши на состояния**

![Меню при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303 013_MenuHover")<br />Пункт меню при наведении курсора мыши

![Меню при наведении указателя мыши проверяется](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303 014_MenuHoverChecked")<br />Проверка элемента меню при наведении курсора мыши

![Меню при наведении указателя мыши выбранных](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303 015_MenuHoverSelected")<br />Выбранный пункт меню при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandBarMenuItemMouseOver` |
| Передний план (текст) | `Environment.CommandBarMenuItemMouseOver` |
| Передний план (глиф подменю) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Флажок | `Environment.CommandBarCheckBoxMouseOver` |
| Фон флажка | `Environment.CommandBarHoverOverSelectedIcon` |
| Фон значка | `Environment.CommandBarHoverOverSelected` |
| Граница значка | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Пункты меню: отключенном состоянии**

![Неактивное меню](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303 016_MenuDisabled")<br />Отключенный элемент меню

![Неактивное меню проверяется](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303 017_MenuDisabledChecked")<br />Отключенный элемент меню с флажком

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Передний план (текст) | `Environment.CommandBarTextInactive` |
| Передний план (глиф подменю) | `Environment.CommandBarMenuSubmenuGlyph` |
| Флажок | `Environment.CommandBarCheckBoxDisabled` |
| Фон флажка | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Панели команд
Панель команд может появляться в нескольких местах, интегрированной среды разработки Visual Studio, прежде всего командная полка и инструментов или окна документов.

Как правило, следует всегда использовать стандартную реализацию панели команд, предоставляемую средой Visual Studio. Использование стандартного механизма обеспечивает правильное отображение визуальных элементов и согласованное поведение интерактивных элементов и других элементов управления панели команд Visual Studio. Однако если вам необходимо создать собственную панель команд, следует правильно оформить ее с помощью указанных ниже имен токенов.

![Красная линия панели команд](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303 018_CommandBarRedline")<br />Панели команд (красная линия)

![Красная линия кнопки переполнения](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303 019_OverflowButtonRedline")<br />Кнопка переполнения (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … в местах, где требуется внедренная команда панель, но не смогут использовать стандартную реализацию панели команд Visual Studio. | … для элементов пользовательского интерфейса, которые не похоже на панель команд. |
| | … для компонентов панели команд, кроме тех, для которых определены имена токенов. |

#### <a name="command-bar-groups"></a>Группы панели команд
Группа панели команд состоит из связанного набора элементов управления панели команд и может содержать любое количество кнопок, разворачивающихся кнопок, раскрывающихся меню, полей со списками или меню. Цвета этих элементов управления определяются отдельными именами токенов, которые рассматриваются в других частях этого руководства. Разделительная линия служит для разделения группы на панели команд в связанные подгруппы.

![Красная линия группа панели команд](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303 020_CommandBarGroupRedline")<br />Группа панели команд (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … в местах, где требуется внедренная команда панель, но не смогут использовать стандартную реализацию панели команд Visual Studio. | … для элементов пользовательского интерфейса, которые не похоже на панель команд. |
| | … для компонентов панели команд, кроме тех, для которых определены имена токенов. |

**Группа панели команд: состояние по умолчанию**

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandBarGradientBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Border | `Environment.CommandBarToolBarBorder` |
| Маркер перетаскивания | `Environment.CommandBarDragHandle` |
| Separator | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Значки команд
![Красная линия значка команды](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303 021_CommandIconRedline1")<br />Значок команды (красная линия)

![Красная линия значка команды с текстом](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303 022_CommandIconRedline2")<br />Значок команды с текстом (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … для кнопок, которые будут размещены на панели команд. | … для элементов управления, которые имеют собственные имена токенов. |
| | ... в любые кроме указанного сочетания фона и цвета переднего плана. |

**Значок команды: состояние по умолчанию**

![Команда значок по умолчанию](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303 023_CommandIconDefault")<br />Значок команды по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Н/Д (наследуется от фона панели команд) |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Border | Н/Д |

**Значок команды: состояние, выбранные по умолчанию**

![По умолчанию, значок выбранной команды](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")<br />По умолчанию, значок выбранной команды

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandBarSelected` |
| Передний план (текст) | `Environment.CommandBarTextSelected` |
| Border | `Environment.CommandBarSelectedBorder` |

**Значок команды: при наведении курсора мыши или фокус состояний**

![Значок команды при наведении курсора мыши или фокус](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303 025_CommandIconHover")<br />Значок команды при наведении курсора мыши или фокус

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Border | `Environment.CommandBarBorder` |

**Значок команды: при наведении курсора мыши или фокус состояний, выбранных**

![Выбрать значок команды при наведении курсора мыши или фокус](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303 026_CommandIconHoverSelected")<br />Значок выбранной команды при наведении курсора мыши или фокус

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandBarHoverOverSelected` |
| Передний план (текст) | `Environment.CommandBarTextHoverOverSelected` |
| Border | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Значок команды: нажат**

![Нажата значок команды](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303 027_CommandIconPressed")<br />Активный значок команды

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.CommandBarTextMouseDown` |
| Border | `Environment.CommandBarBorder` |

**Значок команды: отключенном состоянии**

![Неактивный значок команды](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303 028_CommandIconDisabled")<br />Неактивный значок команды

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Н/Д (наследуется от фона панели команд) |
| Передний план (текст) | `Environment.CommandBarTextInactive` |
| Border | Н/Д |

#### <a name="BKMK_CommandComboBox"></a> Списком панели команд

> [!IMPORTANT]
> Поле со списком похоже на раскрывающийся список, но включает область для ввода и редактирования текста. Если раскрывающийся список не включает область для ввода и редактирования текста, используйте токены цветов, указанные для [командной строке раскрывающиеся меню](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Красная линия панели со списком команд](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303 029_ComboBoxRedline")<br />Поле со списком панели команд (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … При построении пользовательского списком. | ... ни для чего вы не должны всегда соответствовать команда Интерфейс панели. |
| … При создании элемент управления панели команд, которая похожа на поле со списком. | … При наличии доступа к оформленного поле со списком. |

**Команда панели со списком поле ввода поля: состояние по умолчанию**

![Команда панели со списком поле ввода поля](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303 030_ComboBoxInputField")<br />Команда панели со списком поле ввода поля

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ComboBoxBackground` |
| Передний план (текст) | `Environment.ComboBoxText` |
| Border | `Environment.ComboBoxBorder` |
| Separator | Без разделителя |

**Кнопка раскрывающегося списка на панели команд: состояние по умолчанию**

![Раскрывающееся поле со списком&#45;нажатой кнопку](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")<br />Кнопка раскрывающегося списка на панели команд

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Н/Д (наследуется от фона панели команд) |
| Передний план (глиф) | `Environment.ComboBoxGlyph` |

**Команда панели стрелку раскрывающегося списка: состояние по умолчанию**

![Командной строке с раскрывающимся списком](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")<br />Командной строке с раскрывающимся списком

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ComboBoxPopupBackgroundBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.ComboBoxItemText` |
| Border | `Environment.ComboBoxPopupBorder` |

**Команда панели со списком поле ввода поля: наведите указатель мыши на состояния**

![Команда панели поле ввода поля со списком при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br />Команда панели поле ввода поля со списком при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.ComboBoxMouseOverText` |
| Border | `Environment.ComboBoxMouseOverBorder` |
| Separator | `Environment.ComboBoxMouseOverSeparator` |

 **Кнопка раскрывающегося списка на панели команд: наведите указатель мыши на состояния**

![Кнопка раскрывающегося списка на панели команд при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")<br />Кнопка раскрывающегося списка на панели команд при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ComboBoxButtonMouseOverBackground` |
| Передний план (глиф) | `Environment.ComboBoxMouseOverGlyph` |

**Команда панели стрелку раскрывающегося списка: наведите указатель мыши на состояния**

 ![Список раскрывающегося списка панели команд при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")<br />Список раскрывающегося списка панели команд при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон (пункт меню) | `Environment.ComboBoxItemMouseOverBackground` |
| Передний план (текст) | `Environment.ComboBoxItemMouseOverText` |
| Граница (пункт меню) | `Environment.ComboBoxItemMouseOverBorder` |

 **Команда панели со списком поле ввода поля: состояние с фокусом ввода**

![Поле ввода поля со списком на панели команд с фокусом ввода](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br />Командной строке входной поле поля со списком с фокусом ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ComboBoxFocusedBackground` |
| Передний план (текст) | `Environment.ComboBoxFocusedText` |
| Border | `Environment.ComboBoxFocusedBorder` |
| Separator | `Environment.ComboBoxFocusedButtonSeparator` |

**Кнопка раскрывающегося списка на панели команд: состояние с фокусом ввода**

![Кнопка раскрывающегося списка на панели команд с фокусом ввода](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")<br />Фокус командной панели кнопку раскрывающегося списка

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ComboBoxFocusedButtonBackground` |
| Передний план (глиф) | `Environment.ComboBoxFocusedGlyph` |

 **Команда панели со списком поле ввода поля: нажат**

![Нажата командной строке поле ввода поля со списком](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br />Нажата командной строке поле поля со списком ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ComboBoxMouseDownBackground` |
| Передний план (текст) | `Environment.ComboBoxMouseDownText` |
| Border | `Environment.ComboBoxMouseDownBorder` |
| Separator | `Environment.ComboBoxMouseDownSeparator` |

**Кнопка раскрывающегося списка на панели команд: нажат**

![Нажата кнопка раскрывающегося списка на панели команд](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")<br />Нажата кнопка раскрывающегося списка на панели команд

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ComboBoxButtonMouseDownBackground` |
| Передний план (глиф) | `Environment.ComboBoxMouseDownGlyph` |

**Команда панели со списком поле ввода поля: отключенном состоянии**

![Поле ввода поля со списком на панели команд отключена](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br />Отключенные панели поле ввода поля со списком команд

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ComboBoxDisabledBackground` |
| Передний план (текст) | `Environment.ComboBoxDisabledText` |
| Border | `Environment.ComboBoxDisabledBorder` |
| Separator | Без разделителя |

**Кнопка раскрывающегося списка на панели команд: отключенном состоянии**

![Отключить кнопку раскрывающегося списка на панели команд](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")<br />Отключенной командной панели кнопку раскрывающегося списка

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Нет |
| Передний план (глиф) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="BKMK_CommandDropDown"></a> Раскрывающиеся панели команд

> [!IMPORTANT]
> Раскрывающийся список похож на поле со списком, но не имеет области для ввода и редактирования текста. Если раскрывающийся список включает область для ввода и редактирования текста, используйте токены цветов, указанные для [командной строке поля со списком](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Команды панели раскрывающегося списка (красная линия)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303 042_DropdownRedline")<br />Команды панели раскрывающегося списка (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … При создании пользовательского раскрывающегося списка элементов управления. | … для параметров, которые не аналогичную стрелку раскрывающегося списка. |
| | … для полях со списками или разворачивающихся кнопок. |

**Поле выбора раскрывающегося списка командной строке: состояние по умолчанию**

![По умолчанию поле выбора раскрывающегося списка на панели команд](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303 043_DropdownSelectionField")<br />Поле выбора раскрывающегося списка строке команды по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.DropDownBackground` |
| Передний план (текст) | `DropDownText` |
| Border | `DropDownBorder` |
| Separator | Без разделителя |

**Кнопка раскрывающегося списка на панели команд: состояние по умолчанию**

![По умолчанию панели кнопку раскрывающегося списка команд](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303 044_DropdownButton")<br />Кнопка раскрывающегося списка на панели команд по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Нет |
| Передний план (глиф) | `Environment.DropDownGlyph` |

**Команда панели стрелку раскрывающегося списка: состояние по умолчанию**

![По умолчанию в раскрывающемся списке на панели команд](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303 045_DropdownList")<br />По умолчанию командной строке с раскрывающимся списком

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.DropDownPopupBackgroundBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.ComboBoxItemText` |
| Border | `Environment.DropDownPopupBorder` |
| Тень | `Environment.DropShadowBackground` |

**Поле выбора раскрывающегося списка командной строке: наведите указатель мыши на состояния**

![Поле выбора раскрывающегося списка панели команд при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br />Поле выбора раскрывающегося списка панели команд при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.DropDownMouseOverBackgroundBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.DropDownMouseOverText` |
| Border | `Environment.DropDownMouseOverBorder` |
| Separator | `Environment.DropDownButtonMouseOverSeparator` |

**Кнопка раскрывающегося списка на панели команд: наведите указатель мыши на состояния**

![Кнопка раскрывающегося списка на панели команд при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303 047_DropdownButtonHover")<br />Кнопка раскрывающегося списка на панели команд при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.DropDownButtonMouseOverBackground` |
| Передний план (глиф) | `Environment.DropDownMouseOverGlyph` |

**Команда панели стрелку раскрывающегося списка: наведите указатель мыши на состояния**

![Список раскрывающегося списка панели команд при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303 048_DropdownListHover")<br />Список раскрывающегося списка панели команд при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон (пункт меню) | `Environment.ComboBoxItemMouseOverBackground` |
| Передний план (текст) | `Environment.ComboBoxItemMouseOverText` |
| Граница (пункт меню) | `Environment.ComboBoxItemMouseOverBorder` |

 **Поле выбора раскрывающегося списка командной строке: нажат**

![DROP&#45;вниз поле выбора нажата](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br />Нажата командной строке поле выбора раскрывающегося списка

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.DropDownMouseDownBackground` |
| Передний план (текст) | `Environment.DropDownMouseDownText` |
| Border | `Environment.DropDownMouseDownBorder` |
| Separator | `Environment.DropDownButtonMouseDownSeparator` |

**Кнопка раскрывающегося списка на панели команд: нажат**

![Нажата кнопка раскрывающегося списка на панели команд](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")<br />Нажата кнопка раскрывающегося списка на панели команд

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.DropDownButtonMouseDownBackground` |
| Передний план (глиф) | `Environment.DropDownMouseDownGlyph` |

**Поле выбора раскрывающегося списка командной строке: отключенном состоянии**

![Поле выбора раскрывающегося списка на панели команд отключена](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")<br />Отключенные панели поле выбора раскрывающегося списка команд

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.DropDownDisabledBackground` |
| Передний план (текст) | `Environment.DropDownDisabledText` |
| Border | `Environment.DropDownDisabledBorder` |
| Separator | Без разделителя |

**Кнопка раскрывающегося списка на панели команд: отключенном состоянии**

![Отключить кнопку раскрывающегося списка на панели команд](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")<br />Отключенной командной панели кнопку раскрывающегося списка

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Н/Д |
| Передний план (глиф) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Панель команд разворачивающиеся кнопки
Для разворачивающихся кнопок используются многие имена токенов, определенные для других элементов управления панели команд, таких как кнопки, меню и текст панели команд. Все необходимые имена токенов для действий и кнопок раскрывающихся списков приводятся здесь еще раз для удобства. Выберите в раскрывающемся списки разворачивающихся кнопок являются реализацией [командной строке меню](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

![Красная линия разворачивающейся кнопки](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303 053_SplitButtonRedline")<br />Панель команд Разворачивающаяся кнопка (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … При создании пользовательской разворачивающейся кнопки. | … для других видов кнопок. |
| | ... в любые кроме указанного сочетания фона и цвета переднего плана. |

**Панель команд Разворачивающаяся кнопка: состояние по умолчанию**

![По умолчанию в командной строке Разворачивающаяся кнопка](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303 054_SplitButton")<br />Панели команд по умолчанию Разворачивающаяся кнопка

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Нет |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Environment.CommandBarSplitButtonGlyph` |
| Border | Н/Д |
| Separator | Н/Д |

**Панель команд Разворачивающаяся кнопка: наведите указатель мыши на состояния**

![Панель команд Разворачивающаяся кнопка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303 055_SplitButtonHover")<br />Панель команд Разворачивающаяся кнопка при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Передний план (глиф) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Border | `Environment.CommandBarBorder` |
| Separator | `Environment.CommandBarSplitButtonSeparator` |

**Панель команд Разворачивающаяся кнопка: нажат**

![Команда панели Разворачивающаяся кнопка нажата](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303 056_SplitButtonPressed")<br />Панели разворачивающуюся кнопку в нажатом состоянии команд

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.CommandBarTextMouseDown` |
| Передний план (глиф) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Border | `Environment.CommandBarBorder` |
| Separator | Н/Д |

**Панель команд Разворачивающаяся кнопка: отключенном состоянии**

![Отключить командной строке Разворачивающаяся кнопка](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br />Кнопка разделения отключенной командной строки

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Н/Д |
| Передний план (текст) | `Environment.ComboBoxItemTextInactive` |
| Передний план (глиф) | `Environment.CommandBarTextInactive` |
| Border | Н/Д |
| Separator | Н/Д |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Кнопки «Дополнительно» и «Переполнение» панели
Кнопка "Дополнительно" используется, если группа панели команд может настраиваться путем добавления или удаления связанных кнопок. Кнопка "Переполнение" появляется, если панель команд усекается из-за отсутствия места по горизонтали. При ее нажатии открывается меню, содержащее кнопки, которые не поместились на панели команд. Цвета этих двух кнопок определяются одним и тем же набором имен токенов.

![Кнопка «Дополнительные параметры» на панели команд (красная линия)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303 058_MoreOptionsRedline")<br />Кнопка «Дополнительные параметры» на панели команд (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … для пользовательских «Дополнительно» и «Переполнение» кнопок. | … для кнопок, которые не имеют схожие функции кнопке «Переполнение» или «Дополнительно». |

**На панели «Дополнительно» и «Overflow» кнопки команд: состояние по умолчанию**

![По умолчанию кнопка «Дополнительные параметры» на панели команд](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303 059_MoreOptions")<br />Кнопка «Дополнительные параметры» по умолчанию панель команд

![По умолчанию кнопка «Переполнение» на панели команд](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303 060_Overflow")<br />По умолчанию кнопка «Переполнение» на панели команд

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandBarOptionsBackground` |
| Передний план (глиф) | `Environment.CommandBarOptionsGlyph` |

**На панели «Дополнительно» и «Overflow» кнопки команд: наведите указатель мыши на состояния**

![Кнопка «Дополнительные параметры» при наведении курсора мыши на панели команд](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303 061_MoreOptionsHover")<br />Команды панели кнопку «Дополнительные параметры» при наведении курсора мыши

![«Overflow» кнопка на панели команд при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303 062_OverflowOptions")<br />«Overflow» кнопка на панели команд при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (глиф) | `Environment.CommandBarOptionsMouseDownGlyph` |

**На панели «Дополнительно» и «Overflow» кнопки команд: нажат**

![Нажата кнопка «Дополнительные параметры» на панели команд](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303 063_MoreOptionsPressed")<br />Нажата кнопка «Дополнительные параметры» на панели команд

![Переполнение при нажатии](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303 064_OverflowPressed")<br />Нажата кнопка «Переполнение» на панели команд

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (глиф) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Окна документов
Нет воссоздавать окна документов, не нужно, так как они предоставляются средой Visual Studio. Однако может потребоваться использовать цвета, применяемые в окнах документов, чтобы ваш пользовательский интерфейс был согласован с этой частью среды Visual Studio.

При использовании токенов цветов окна документов, будьте внимательны использовать их только для аналогичных элементов и всегда в парах. Если не сделать этого, можно получить непредвиденные результаты в пользовательском Интерфейсе.

### <a name="document-window-frames"></a>Рамки окон документа
Окна документов могут быть закрепленными в интегрированной среде разработки или перемещаемыми как отдельные окна. Если окно документа является перемещаемой вне интегрированной среды разработки, он по-прежнему находится в контейнере документа и имеет фона, границы, текста и цвета, которые являются так же, как, когда он является частью интегрированной среды разработки. Однако документ размещается внутри рамки, которая имеет собственные цвета фона, границы и текста. Если в контейнере документа закреплены окна инструментов, они наследуют поведение и цвет вкладок от имен токенов окна документа.

![Закрепленное окно документа (красная линия)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")<br />Закрепленное окно документа (красная линия)

![Плавающее окно (красная линия)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")<br />Плавающее окно (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … в любом месте вы создаете пользовательский Интерфейс, который вы хотите обеспечить поиск окна документа. | … для пользовательского интерфейса, который вы не хотите автоматически изменить, если у оболочки имеется темы. |

**Окно документа закрепленными или с плавающей запятой: состояние по умолчанию**

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Зависит от типа документа |
| Передний план (текст) | Зависит от типа документа |
| Border | `Environment.ToolWindowBorder` |

**Фокус, плавающий фрейм окна документа: состояние по умолчанию**

![По умолчанию с фокусом ввода, плавающий фрейм окна документа](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303 067_FrameFocused")<br />По умолчанию с фокусом ввода, плавающий фрейм окна документа

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ToolWindowFloatingFrame` |
| Передний план (текст) | `Environment.ToolWindowFloatingFrame` |
| Передний план (глиф) | `Environment.RaftedWindowButtonActiveGlyph` |
| Border | `Environment.MainWindowActiveDefaultBorder` |
| Граница (глиф) | `Environment.RaftedWindowButtonActiveBorder`<br />(Задается как прозрачная) |

**Рамка окна документа без фокуса ввода, с плавающей запятой: состояние по умолчанию**

![Рамка окна документа без фокуса ввода, с плавающей запятой по умолчанию](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303 068_FrameUnfocused")<br />По умолчанию рамка окна документа без фокуса ввода, с плавающей запятой

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ToolWindowFloatingFrameInactive` |
| Передний план (текст) | `Environment.ToolWindowFloatingFrameInactive` |
| Передний план (глиф) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Border | `Environment.MainWindowInactiveBorder` |
| Граница (глиф) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Задается как прозрачная) |

**Фокус, плавающий фрейм окна документа: наведите указатель мыши на состояния**

![Фокус, плавающий фрейм окна документа при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303 069_FrameFocusedHover")<br />Фокус, плавающий фрейм окна документа при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон (глиф) | `Environment.RaftedWindowButtonHoverActive` |
| Передний план (глиф) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Граница (глиф) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Рамка окна документа без фокуса ввода, с плавающей запятой: наведите указатель мыши на состояния**

![Рамка окна документа без фокуса ввода, с плавающей запятой при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303 070_FrameUnfocusedHover")<br />Без фокуса ввода, плавающий фрейм окна документа при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон (глиф) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Передний план (глиф) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Граница (глиф) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Фокус, плавающий фрейм окна документа: нажат**

![Ориентированных и с плавающей запятой рамка окна документа на клавишу](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303 071_FrameFocusedPressed")<br />Ориентированных и с плавающей запятой рамка окна документа на клавишу

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон (глиф) | `Environment.RaftedWindowButtonDown` |
| Передний план (глиф) | `Environment.RaftedWindowButtonDownGlyph` |
| Граница (глиф) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Вкладки документов
Вкладки документов размещаются в канале вкладок и указывают, какие документы в настоящее время открыты, а также какой документ в настоящий момент выбран или активен. Окна инструментов также могут закрепляться в канале вкладок документов, если пользователь размещает их там. В этом случае для них используются те же цвета, что и для окон документов. Если вы создаете пользовательский интерфейс, цвета которого должны всегда соответствовать цветам окна документа (в том числе при обновлении темы или установке новых тем), то используйте ссылки на указанные ниже токены цветов.

![Вкладки документов (красная линия)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303 072_DocumentTabRedline")<br />Вкладки документов (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … в любом месте вы создаете пользовательский Интерфейс, который будет соответствовать вкладкам документов и автоматически изменяться при обновлении тем или добавлении новых цветов темы. | … для пользовательского интерфейса, который вы не хотите изменить автоматически, если оболочка имеет темы. |

#### <a name="open-document-tabs"></a>Вкладки открытых документов
Каждый открытый документ имеет вкладку в канале вкладок документов, на которой показано его имя. Документы могут быть либо выбраны, либо открыты в фоновом режиме. На их вкладках указываются перечисленные ниже состояния.

- Выбранная вкладка представляет документ, который в настоящее время отображается в контейнере документа. Выбранная вкладка имеет границу документа, которая располагается по верхнему краю контейнера документа.

- Фоновые вкладки — это все вкладки документов, кроме выбранной в настоящий момент вкладки. При щелчке по такой вкладке она становится выбранной и получает цвета фона, границы и текста с соответствующими именами токенов.

![Открытой вкладки документов (красная линия)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")<br />Открытой вкладки документов (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … При создании пользовательских вкладок документов. | … для вкладок оговоренные предварительно (Предварительная версия). |
| | … для пользовательского интерфейса, который вы не хотите изменить автоматически, если у оболочки имеется темы. |

**Вкладки документов выбранного, фокусом ввода**

![Вкладки документов с фокусом ввода, выбран](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303 074_SelectedTabFocused")<br />Вкладки документов выбранного, фокусом ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.FileTabSelectedGradientTop`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.FileTabSelectedText` |
| Border | `Environment.FileTabSelectedBorder`<br />(Значение совпадает с цветом фона). |
| Граница документа | `Environment.FileTabDocumentBorderBackground` |

**Вкладки документов выбранного, без фокуса ввода**

![Вкладки документов выбранного, без фокуса ввода](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br />Вкладки документов выбранного, без фокуса ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.FileTabInactiveGradientTop`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.FileTabInactiveText` |
| Border | `Environment.FileTabInactiveBorder`<br />(Значение совпадает с цветом фона). |
| Граница документа | `Environment.FileTabInactiveDocumentBorderBackground` |

**Вкладка фона документа: состояние по умолчанию**

![Вкладка документа по умолчанию фона](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303 076_BackgroundTab")<br />Вкладка документа фона по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.FileTabBackground` |
| Передний план (текст) | `Environment.FileTabText` |
| Border | `Environment.FileTabBorder`<br />(Значение совпадает с цветом фона). |

**Вкладка фона документа: наведите указатель мыши на состояния**

![Вкладка фона документа при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303 077_BackgroundTabHover")<br />Вкладка фона документа при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.FileTabHotGradientTop`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.FileTabHotText` |
| Border | `Environment.FileTabHotBorder`<br />(Значение совпадает с цветом фона). |

#### <a name="preview-tab"></a>Вкладка предварительного просмотра
Также называется «предварительный» вкладку. Вкладка предварительного просмотра отображается в правой части канала вкладок документов, когда пользователь щелкает элемент в окне инструментов обозревателя решений. Она служит для предварительного просмотра документа и дает пользователю возможность сохранять документ открытым в левой части канала вкладок документов. Одновременно может быть открыта только одна вкладка предварительного просмотра. Так же как открытые вкладки, вкладки предварительного просмотра имеют как фоновое, так и выбранное состояния и в активном состоянии могут получать фокус ввода и терять его.

![Вкладка предварительного просмотра (красная линия)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303 078_PreviewTabRedline")<br />Вкладка предварительного просмотра (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … в любом месте, вы создаете Предварительный просмотр и какой-либо элемент в соответствии с текущей цвета вкладки предварительного просмотра. | … для любого документа или вкладки, которая не является временной (Предварительная версия). |
| | … для пользовательского интерфейса, который вы не хотите изменить автоматически, если у оболочки имеется темы. |

**Вкладка предварительного просмотра фокусом, выделенным**

![Вкладка предварительного просмотра фокусом, выделенным](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303 079_PreviewTabFocused")<br />Вкладка предварительного просмотра фокусом, выделенным

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.FileTabProvisionalSelectedActive` |
| Передний план (текст) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Border | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Значение совпадает с цветом фона). |
| Граница документа | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Вкладка предварительного просмотра без фокуса ввода, выделенным**

![Вкладка предварительного просмотра без фокуса ввода, выделенным](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br />Вкладка предварительного просмотра без фокуса ввода, выделенным

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.FileTabProvisionalSelectedInactive` |
| Передний план (текст) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Border | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Граница документа | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Фоновая вкладка предварительного просмотра: состояние по умолчанию**

![Фоновая вкладка предварительного просмотра по умолчанию](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303 081_PreviewBackgroundTab")<br />Фоновая вкладка предварительного просмотра по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.FileTabProvisionalInactive` |
| Передний план (текст) | `Environment.FileTabProvisionalInactiveForeground` |
| Border | `Environment.FileTabProvisionalInactiveBorder`<br />(Значение совпадает с цветом фона). |

**Фоновая вкладка предварительного просмотра: при наведении указателя мыши на состояния**

![Фоновая вкладка предварительного просмотра при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")<br />Фоновая вкладка предварительного просмотра при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.FileTabProvisionalHover` |
| Передний план (текст) | `Environment.FileTabProvisionalHoverForeground` |
| Border | `Environment.FileTabProvisionalHoverBorder`<br />(Значение совпадает с цветом фона). |

#### <a name="document-overflow-button"></a>Кнопка переполнения документа
Кнопка переполнения документа присутствует, если открыт один или несколько документов, вне зависимости от того, имеется ли в текущей конфигурации пространство по вертикали для размещения всех вкладок документов. Выберите в раскрывающемся меню переполнения документа, которая управляется [командной строке меню](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) цветов, отображает список всех открытых документах, как видимых, так и скрытых и глиф переполнения меняется в зависимости от того, являются ли все открытые документы отображается в канале вкладок.

![Кнопка переполнения документа (красная линия)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303 083_OverflowRedline")<br />Кнопка переполнения документа (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … При создании пользовательской кнопки переполнения документа. | … для пользовательского интерфейса, не аналогичную кнопки переполнения. |
| | … для кнопок переполнения панели команд. |

**Кнопка переполнения документа: состояние по умолчанию**

![Кнопка переполнения документа по умолчанию](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303 084_Overflow")<br />Кнопка переполнения документа по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.DocWellOverflowButtonBackground` |
| Передний план (глиф) | `Environment.DocWellOverflowButtonGlyph` |
| Border | Н/Д |

**Кнопка переполнения документа: наведите указатель мыши на состояния**

![Кнопка переполнения документа при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303 085_OverflowHover")<br />Кнопка переполнения документа при наведении указателя

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Передний план (глиф) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Border | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Кнопка переполнения документа: нажат**

![Кнопка переполнения документа на материалах издательства press](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303 086_OverflowPressed")<br />Кнопка переполнения документа на материалах издательства press

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Передний план (глиф) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Border | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Добавление тегов
Visual Studio поддерживает добавление тегов, что позволяет пользователю объявлять доступные для поиска ключевые слова в целях отслеживания. Например, руководители проектов и разработчики могут использовать Team Foundation Server (TFS) для добавления тегов к рабочим элементам. В приведенных ниже таблицах представлены имена цветов как для самого тега, так и для глифа (значка закрытия), который появляется при наведении указателя и в некоторых состояниях.

![Добавление тегов в Visual Studio (красная линия)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303 176_TaggingRedline")<br />Добавление тегов в Visual Studio (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … для пользовательского интерфейса, который поддерживает добавление тегов. | … для любого другого типа пользовательского интерфейса. |

#### <a name="tags"></a>Теги

**"Тег": состояние по умолчанию**

![Тег по умолчанию](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303 177_Tag")<br />Тег по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Tag.Background` |
| Передний план (текст) | `Tag.Background` |

**"Тег": состояние при наведении указателя мыши**

![Тег при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303 178_TagHover")<br />Тег при наведении указателя мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Tag.HoverBackground` |
| Передний план (текст) | `Tag.HoverBackgroundText` |

**Тег: нажат.**

![Нажата тега](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303 179_TagPressed")<br />Тег в нажатом состоянии

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Tag.PressedBackground` |
| Передний план (текст) | `Tag.PressedBackgroundText` |

**"Тег": выбранное состояние**

![Выбран тег](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303 180_TagSelected")<br />Выбранный тег

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Tag.SelectedBackground` |
| Передний план (текст) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Закрыть (&times;) тег глифа

**Закрыть (&times;) тег глифа: состояние по умолчанию**

![По умолчанию Close (&times;) тег глифа](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303 181_TagGlyph")<br />По умолчанию Close (&times;) тег глифа

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Н/Д |
| Передний план (глиф) | `Tag.TagHoverGlyph` |

**Закрыть (&times;) тег глифа: наведите указатель мыши на состояния**

![Закрыть (&times;) тега при наведении курсора мыши глиф](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303 182_TagGlyphHover")<br />Закрыть (&times;) тега глиф при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Tag.TagHoverGlyphHoverBackground` |
| Передний план (глиф) | `Tag.TagHoverGlyphHover` |
| Border | `Tag.TagHoverGlyphHoverBorder` |

**Закрыть (&times;) тег глифа: нажат**

![Нажата Close (&times;) тег глифа](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303 183_TagGlyphPressed")<br />Нажата Close (&times;) тег глифа

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Tag.TagHoverGlyphPressedBackground` |
| Передний план (глиф) | `Tag.TagHoverGlyphPressed` |
| Border | `Tag.TagHoverGlyphPressedBorder` |

**Выбран тег с Close (&times;) глифа: состояние по умолчанию**

![Выбранный тег с закрытия по умолчанию (&times;) глифа](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303 184_TagSelected")<br />Выбранный тег с закрытия по умолчанию (&times;) глифа

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Н/Д |
| Передний план (глиф) | `Tag.TagSelectedGlyph` |

**Выбран тег с Close (&times;) глифа: наведите указатель мыши на состояния**

![Выбран тег с Close (&times;) глиф при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303 185_TagSelectedHover")<br />Выбран тег с Close (&times;) глиф при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Tag.TagSelectedGlyphHoverBackground` |
| Передний план (глиф) | `Tag.TagSelectedGlyphHover` |
| Border | `Tag.TagSelectedGlyphHoverBorder` |

**Выбран тег с Close (&times;) глифа: нажат**

![Выбран, нажата тег с Close (&times;) глифа](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303 186_TagSelectedPressed")<br />Выбран, нажата тег с Close (&times;) глифа

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Tag.TagSelectedGlyphPressedBackground` |
| Передний план (глиф) | `Tag.TagSelectedGlyphPressed` |
| Border | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Окна инструментов
Нет воссоздавать окна инструментов, не нужно, так как они предоставляются средой Visual Studio. Однако может потребоваться использовать цвета, применяемые в окнах инструментов, чтобы ваш пользовательский интерфейс был согласован с этой частью среды Visual Studio.

![Окно инструментов (красная линия)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303 087_ToolWindowRedline")<br />Окно инструментов (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … в любом месте вы создаете пользовательский Интерфейс, который вы хотите обеспечить поиск окна инструментов. | … для пользовательского интерфейса, который вы не хотите изменить автоматически, если у оболочки имеется темы. |

### <a name="tool-window-frame"></a>Рамка окна инструментов
Окна инструментов в Visual Studio используются для множества различных задач и могут иметь одно из нескольких состояний. Если окно инструментов открыто, оно может быть назначено одной из четырех сторон области документа. Окна инструментов также могут перемещаться за пределы интегрированной среды документов, что позволяет размещать их в любом месте экрана. Перемещаемые окна всегда находятся поверх интегрированной среды разработки. Наконец, окна инструментов могут закрепляться как окна документов и отображаться в виде вкладок в контейнере документа. К окнам инструментов, закрепленным как окна документов, частично применяются имена токенов окна документа.

![Рамка окна инструментов (красная линия)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")<br />Рамка окна инструментов (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … в любом месте вы создаете пользовательский Интерфейс, который вы хотите обеспечить поиск окна инструментов. | … для пользовательского интерфейса, который вы не хотите изменить автоматически, если у оболочки имеется темы. |

**Закрепленное окно**

![Закрепленное окно](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303 089_ToolWindowDocked")<br />Закрепленное окно

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ToolWindowBackground` |
| Border | `Environment.ToolWindowBorder` |

**С плавающей запятой, окно инструментов с фокусом ввода**

![С плавающей запятой, окно инструментов с фокусом ввода](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303 090_ToolWindowFocused")<br />С плавающей запятой, окно инструментов с фокусом ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ToolWindowBackground` |
| Border | `Environment.MainWindowActiveDefaultBorder` |

**С плавающей запятой, окна инструментов без фокуса ввода**

![Окно инструментов с плавающей запятой, без фокуса ввода](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303 091_ToolWindowUnfocused")<br />С плавающей запятой, окна инструментов без фокуса ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ToolWindowBackground` |
| Border | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Панели инструментов в стиле windows
Панели элементов является одним из наиболее часто используемых стандартных окон инструментов в Visual Studio. Это по сути дерево с помощью специальной темой и применения стилей.

![Окно панели элементов по принципу (красная линия)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303 189_ToolboxRedline")<br />Окно панели элементов по принципу (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … При создании окна инструментов, которое вы хотите всегда должно быть согласовано с панелью элементов оболочки. | … для параметров, которые не похожи на панель элементов пользовательского интерфейса или если вы не уверены, ли пользовательский Интерфейс будет иметь проблемы при изменении цветов панели элементов оболочки. |

**Узлы элементов: состояние по умолчанию**

![Родительский узел панели инструментов по умолчанию](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303 190_ToolboxParentNode")<br />Родительский узел панели инструментов по умолчанию

![Дочерний узел панели инструментов по умолчанию](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303 191_ToolboxChildNode")<br />Дочерний узел панели инструментов по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ToolboxContent`<br />(Заголовки) |
| Фон | `Environment.ToolWindowBackground`<br />(Отдельные элементы или все окно, если нет доступных элементов управления) |
| Border | Нет |
| Передний план (глиф) | `Environment.ToolboxContent` |
| Передний план (текст) | `Environment.ToolboxContent` |

**Дочерние узлы элементов: наведите указатель мыши на состояния**

![Дочерний узел панели инструментов при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")<br />Дочерний узел панели инструментов при наведении указателя мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ToolboxContentMouseOver`<br />(Только для отдельных элементов) |
| Border | Нет |
| Передний план (текст) | `Environment.ToolboxContentMouseOver`<br />(Только для отдельных элементов) |

**Выбранные узлы элементов: состояние с фокусом ввода**

![Родительский узел панели инструментов фокусом, выделенным](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br />Родительский узел панели инструментов фокусом, выделенным

![Дочерний узел панели инструментов фокусом, выделенным](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br />Дочерний узел панели инструментов фокусом, выделенным

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `TreeView.SelectedItemActive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Border | `TreeView.FocusVisualBorder`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Передний план (глиф) | `TreeView.SelectedItemActive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Передний план (текст) | `TreeView.SelectedItemActive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Выбранные узлы элементов: состояния без фокуса ввода**

![Родительский узел панели инструментов выбранной, без фокуса ввода](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br />Родительский узел панели инструментов выбранной, без фокуса ввода

![Дочерний узел панели инструментов выбранной, без фокуса ввода](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br />Дочерний узел панели инструментов выбранной, без фокуса ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `TreeView.SelectedItemInactive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Border | Нет |
| Передний план (глиф) | `TreeView.SelectedItemInactive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Передний план (текст) | `TreeView.SelectedItemInactive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Заголовок окна инструментов
Граница заголовка окна не true границы, а толстой линией в верхней части заголовка окна. Он не имеет имени токена для состояния без фокуса ввода.

![Заголовок окна инструментов (красная линия)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")<br />Заголовок окна инструментов (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … в любом месте вы создаете пользовательский Интерфейс, который вы хотите обеспечить поиск окна инструментов. | … для пользовательского интерфейса, который вы не хотите изменить автоматически, если у оболочки имеется темы. |

**Строки заголовка с фокусом ввода**

![Строки заголовка с фокусом ввода](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303 093_TitleBarFocused")<br />Заголовок окна с фокусом ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.TitleBarActiveGradientBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.TitleBarActiveText` |
| Border | `Environment.TitleBarActiveBorder`<br />(Значение совпадает с цветом фона). |
| Маркер перетаскивания | `Environment.TitleBarDragHandleActive` |

**Строки заголовка без фокуса ввода**

![Строки заголовка без фокуса ввода](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303 094_TitleBarUnfocused")<br />Заголовок окна без фокуса ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.TitleBarInactiveGradientBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.TitleBarInactiveText` |
| Border | Н/Д |
| Маркер перетаскивания | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Кнопки на панели заголовка окна инструментов
![Строка кнопки заголовка (красная линия)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")<br />Строка кнопки заголовка (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … для кнопок, отображаемых в пользовательском Интерфейсе, использующий токены цветов из панели заголовка окна инструментов. | … для кнопок, отображаемых в других местах. |
| | ... в любые кроме указанного сочетания фона и цвета переднего плана. |

**Кнопки в заголовке окна с фокусом ввода: состояние по умолчанию**

![По умолчанию, кнопки в заголовке окна с фокусом ввода](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")<br />По умолчанию, кнопки в строке заголовка с фокусом ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Н/Д |
| Передний план (глиф) | `Environment.ToolWindowButtonActiveGlyph` |
| Border | Н/Д |

**Кнопки в строке заголовка без фокуса ввода: состояние по умолчанию**

![По умолчанию, кнопки в строке заголовка без фокуса ввода](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")<br />По умолчанию, кнопки в строке заголовка без фокуса ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | Н/Д |
| Передний план (глиф) | `Environment.ToolWindowButtonInactiveGlyph` |
| Border | Н/Д |

**Кнопки в заголовке окна с фокусом ввода: наведите указатель мыши на состояния**

![Кнопки в заголовке окна с фокусом ввода при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")<br />Кнопки в строке заголовка с фокусом ввода при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ToolWindowButtonHoverActive` |
| Передний план (глиф) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Border | `Environment.ToolWindowButtonHoverActiveBorder` |

**Кнопки в строке заголовка без фокуса ввода: наведите указатель мыши на состояния**

![Кнопки в строке заголовка без фокуса ввода при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")<br />Кнопки в строке заголовка без фокуса ввода при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ToolWindowButtonHoverInactive` |
| Передний план (глиф) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Border | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Кнопки в заголовке окна с фокусом ввода: нажат**

![Уделено кнопки в заголовке окна нажмите клавишу](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")<br />Кнопки в строке заголовка с фокусом на материалах издательства press

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ToolWindowButtonDown` |
| Передний план (глиф) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Border | `Environment.ToolWindowButtonDownBorder` |

**Кнопки в строке заголовка без фокуса ввода: нажат**

![Кнопки в строке заголовка без фокуса ввода на материалах издательства press](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")<br />Кнопки в строке заголовка без фокуса ввода на материалах издательства press

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ToolWindowButtonDown` |
| Передний план (глиф) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Border | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Вкладки окна инструментов
![Вкладка окна инструментов (красная линия)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303 102_ToolWindowTabRedline")<br />Вкладка окна инструментов (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … в любом месте вы создаете пользовательский Интерфейс, который вы хотите обеспечить поиск окна инструментов. | … для пользовательского интерфейса, который вы не хотите изменить автоматически, если у оболочки имеется темы. |

**Вкладка окна выбранных инструментов с фокусом ввода**

![Вкладка окна инструментов с фокусом ввода, выбран](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")<br />Выбранная вкладка окна инструментов с фокусом ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ToolWindowTabSelectedTab` |
| Передний план (текст) | `Environment.ToolWindowTabSelectedActiveText` |
| Border | `Environment.ToolWindowTabSelectedBorder`<br />(Значение совпадает с цветом фона). |

**Вкладка окна выбранных инструментов без фокуса ввода**

![Вкладка окна выбранных инструментов без фокуса ввода](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")<br />Выбранная вкладка окна инструментов без фокуса ввода

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ToolWindowTabSelectedTab` |
| Передний план (текст) | `Environment.ToolWindowTabSelectedText` |
| Border | `Environment.ToolWindowTabSelectedBorder`<br />(Значение совпадает с цветом фона). |

**Фоновая вкладка окна инструментов: состояние по умолчанию**

![По умолчанию фоновая вкладка окна инструментов](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")<br />По умолчанию фоновая вкладка окна инструментов

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Ограничения градиента устанавливаются в одно и то же значение цвета в Visual Studio 2013.) |
| Передний план (текст) | `Environment.ToolWindowTabText` |
| Border | `Environment.ToolWindowTabBorder` |

**Фоновая вкладка окна инструментов: наведите указатель мыши на состояния**

![Фоновая вкладка окна инструментов при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")<br />Фоновая вкладка окна инструментов при наведении указателя

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Ограничения градиента устанавливаются в одно и то же значение цвета в Visual Studio 2013.) |
| Передний план (текст) | `Environment.ToolWindowTabMouseOverText` |
| Border | `Environment.ToolWindowTabMouseOverBorder`<br />(Значение совпадает с цветом фона). |

### <a name="auto-hide-tabs"></a>Автоматически скрываемые вкладки

![Вкладки автоматического скрытия (красная линия)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303 107_AutoHideRedline")вкладки автоматического скрытия (красная линия)

| Используйте... | Не используйте... |
| --- | --- |
| … в любом месте вы создаете пользовательский Интерфейс, который вы хотите обеспечить поиск вкладки окна инструментов автоматически скрыто. | … для пользовательского интерфейса, который вы не хотите изменить автоматически, если у оболочки имеется темы. |

**Автоматически скрываемые вкладки: состояние по умолчанию**

![Автоматически скрываемая вкладка по умолчанию](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303 108_AutoHideTab")<br />Автоматически скрываемая вкладка по умолчанию

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.AutoHideTabBackgroundBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.AutoHideTabText` |
| Border | `Environment.AutoHideTabBorder` |

**Автоматически скрываемые вкладки: наведите указатель мыши на состояния**

![Вкладка автоматического скрытия при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303 109_AutoHideTabHover")<br />Вкладка автоматического скрытия при наведении курсора мыши

| Элемент | Имя токена: Category.Color |
| --- | --- |
| Фон | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Ограничения градиента для данного токена, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.AutoHideTabMouseOverText` |
| Border | `Environment.AutoHideTabMouseOverBorder` |
