---
title: "Общие цвета для Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9524ecc3cadef58821fba857de8e82e59eea9b43
ms.openlocfilehash: 027e57a8d6ba4b4d317289cbdb74aa064de2ef4e
ms.contentlocale: ru-ru
ms.lasthandoff: 05/04/2017

---
# <a name="shared-colors-for-visual-studio"></a>Общие цвета для Visual Studio
Если вы разрабатываете пользовательский Интерфейс, который использует стандартные элементы оболочки Visual Studio, или нужно элемента интерфейса для согласования с аналогичными функциями, используйте существующие имена токенов в файлах определения пакетов для выбора и назначения цветов. Таким образом можно обеспечить согласованность пользовательского интерфейса со всей средой Visual Studio и его автоматическое обновление при добавлении или обновлении тем.  

В этом разделе описываются стандартные элементы пользовательского интерфейса и используемые ими имена токенов, на которые можно ссылаться при разработке похожего пользовательского интерфейса. Сведения о том, как получить доступ к этим токенам цветов см [служба VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  

Используйте имена токенов правильно.  

-   **Используйте имена токенов в зависимости от функций, не на сам цвет.** Стандартные общие цвета связаны с определенными элементами интерфейса и предназначены для использования только для аналогичных или похожих функций. Например, не используйте цвет выбранного поля со списком для анимированного индикатора хода выполнения только потому, что вам понравился цвет. Функции, поле со списком и анимированного индикатора различны, и если цвет, связанный с полем со списком, изменится, он может оказаться неподходящим для анимированного элемента. Согласованное использование цветов помогает пользователям ориентироваться в интерфейсе и предотвращает путаницу.  

-   **Используйте цвета фона и текста в правильном сочетании.** Цвет фона, предназначенный для текста, имеет соответствующий цвет текста. Не используйте цвета текста, отличные от тех, которые определены для данного цвета фона. Если не связан цвет текста, не используйте цвет фона для поверхности, на котором предполагается, что для отображения текста. Другие сочетания цветов текста и фона может обернуться интерфейс неудобным для восприятия.  

-   **Используйте цвета элементов управления, которые подходят для их расположение.** В определенных состояниях некоторые элементы управления Visual Studio нет отдельной границы и цвета фона. Эти цвета наследуются от областей, в которых они расположены. Всегда используйте имена токенов, которые подходят для того места, в котором вы размещаете элементы управления.  

> [!IMPORTANT]
> Не используйте токены из категорий «Начальная страница» и «Cider».  

## <a name="common-shared-controls"></a>Стандартные общие элементы управления

При использовании стандартной панели команд Visual Studio в функции, у вас есть доступ к оформленным элементам управления оболочки. Не следует изменять шаблон этих стандартных элементов управления. Однако если вам нужно создать пользовательскую панель команд, вам также может потребоваться создать пользовательские элементы управления. В этом случае используйте правильные имена токенов для каждого из указанных ниже элементов управления, чтобы ваш пользовательский интерфейс был согласован с остальной средой Visual Studio.

### <a name="button-controls"></a>Элементы управления "Кнопка"

![Красная линия кнопки](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303 155_ButtonControlRedline")

| Используйте: | Не используйте: |
| --- | --- |
| ... для кнопок в контейнере документа, которые нужно интегрировать с темами Visual Studio (Light, Темная, Blue или системная высококонтрастная тема). | ... для кнопок, которые будут отображаться на пользовательском фоне, не входящих в тему Visual Studio. |

**Кнопки: стандартные состояния**

![Стандартной кнопки](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Стандартной кнопки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.Button` |
| Граница кнопки | `CommonControls.ButtonBorder` |

**Кнопки: по умолчанию состояние**

![Кнопка по умолчанию](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Кнопка по умолчанию

| Элемент | Имя токена: Category.color | 
| --- | --- | 
| Кнопка | `CommonControls.ButtonDefault` |
| Граница кнопки | `CommonControls.ButtonBorderDefault` |

**Кнопки: отключенное состояние**  

![Неактивная кнопка](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Неактивная кнопка  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.ButtonDisabled` |
| Граница кнопки | `CommonControls.ButtonBorderDisabled` |

**Кнопки: при наведении указателя мыши состояние**  

![Кнопка при наведении курсора мыши](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Кнопка при наведении курсора мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.ButtonHover` |
| Граница кнопки | `CommonControls.ButtonBorderHover` |

**Кнопка: нажата**  

![Кнопка в нажатом состоянии](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Кнопка в нажатом состоянии  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.ButtonPressed` |
| Граница кнопки | `CommonControls.ButtonBorderPressed` |

**Кнопки: конкретное состояние**  

![Кнопка с фокусом ввода](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Кнопка с фокусом ввода  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.ButtonFocused` |
| Граница кнопки | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Элементы управления "Флажок"  
![Флажок (красная линия)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Флажок (красная линия)  

| Используйте: | Не используйте: |
| --- | --- |
| ... для элементов управления "флажок", содержащихся в документе также. | ... для пользовательского интерфейса, который не является элементом управления "флажок". |

**Флажок: состояние по умолчанию**  

![Флажок](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />По умолчанию флажок

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `CommonControls.CheckBoxBackground` |
| Border | `CommonControls.CheckBoxBorder` |
| Text | `CommonControls.CheckBoxText` |
| Глиф | `CommonControls.CheckBoxGlyph` |

**Флажок: в отключенном состоянии**  

![Отключенный флажок](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Отключенный флажок  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `CommonControls.CheckBoxBackgroundDisabled` |
| Border | `CommonControls.CheckBoxBorderDisabled` |
| Text | `CommonControls.CheckBoxTextDisabled` |
| Глиф | `CommonControls.CheckBoxGlyphDisabled` |

**Флажок: наведите указатель мыши состояния**  

 ![Флажок при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Флажок при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `CommonControls.CheckBoxBackgroundHover` |
| Border | `CommonControls.CheckBoxBorderHover` |
| Text | `CommonControls.CheckBoxTextHover` |
| Глиф | `CommonControls.CheckBoxGlyphHover` |  

**Флажок: нажата состояния**  

![Нажатый флажок](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Нажатый флажок  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `CommonControls.CheckBoxBackgroundPressed` |
| Border | `CommonControls.CheckBoxBorderPressed` |
| Text | `CommonControls.CheckBoxTextPressed` |
| Глиф | `CommonControls.CheckBoxGlyphPressed` |  

**Флажок: состояние с фокусом ввода**  

![Конкретное флажок](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Конкретное флажок  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `CommonControls.CheckBoxBackgroundFocused` |
| Border | `CommonControls.CheckBoxBorderFocused` |
| Text | `CommonControls.CheckBoxTextFocused` |
| Глиф | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Раскрывающиеся списки и поля со списком полей
![Раскрывающийся список или списком (красная линия)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Раскрывающийся список или списком (красная линия)  

| Используйте: | Не используйте: |
| --- | --- |
| ... для раскрывающихся списков и полей со списком полей в документе также. | ... для пользовательского интерфейса, которая не находится в поле раскрывающегося списка или поля со списком. |  
| | ... для панели команд [раскрывающихся списков](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) или [поля со списком](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Раскрывающиеся списки и поля со списком полей: состояние по умолчанию**  

![По умолчанию раскрывающегося списка/со списком](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />По умолчанию раскрывающегося списка/со списком

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `CommonControls.ComboBoxBackground` |
| Border | `CommonControls.ComboBoxBorder` |
| Text | `CommonControls.ComboBoxText` |
| Separator | `CommonControls.ComboBoxSeparator` |
| Глиф | `CommonControls.ComboBoxGlyph` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackground` |

**Раскрывающиеся списки и поля со списком полей: в отключенном состоянии**  

![Отключенные раскрывающегося списка/со списком](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Отключенные раскрывающегося списка/со списком

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `CommonControls.ComboBoxBackgroundDisabled` |
| Border | `CommonControls.ComboBoxBorderDisabled` |
| Text | `CommonControls.ComboBoxTextDisabled` |
| Separator | `CommonControls.ComboBoxSeparatorDisabled` |
| Глиф | `CommonControls.ComboBoxGlyphDisabled` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Раскрывающиеся списки и поля со списком полей: наведите указатель мыши состояния**  

![Раскрывающийся список/со списком при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Раскрывающийся список/поле со списком при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `CommonControls.ComboBoxBackgroundHover` |
| Border | `CommonControls.ComboBoxBorderHover` |
| Text | `CommonControls.ComboBoxTextHover` |
| Separator | `CommonControls.ComboBoxSeparatorHover` |
| Глиф | `CommonControls.ComboBoxGlyphHover` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Раскрывающиеся списки и поля со списком полей: нажата состояния**  

![Нажата раскрывающегося списка/со списком](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Нажата раскрывающегося списка/со списком  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `CommonControls.ComboBoxBackgroundPressed` |
| Border | `CommonControls.ComboBoxBorderPressed` |
| Text | `CommonControls.ComboBoxTextPressed` |
| Separator | `CommonControls.ComboBoxSeparatorPressed` |
| Глиф | `CommonControls.ComboBoxGlyphPressed` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Раскрывающиеся списки и поля со списком полей элемента представления списка: нажата состояния**  

 ![Раскрывающийся список/со списком нажатии элемента представления списка](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Раскрывающийся список/со списком нажатии элемента представления списка  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон |  `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Border | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Текст элемента | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Фон с тенью | `CommonControls.ComboBoxListBackgroundShadow` |

**Раскрывающиеся списки и поля со списком полей: состояние с фокусом ввода**  

![Раскрывающийся список/со списком с фокусом](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Раскрывающийся список/со списком с фокусом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `CommonControls.ComboBoxBackgroundFocused` |
| Border | `CommonControls.ComboBoxBorderFocused` |
| Text | `CommonControls.ComboBoxTextFocused` |
| Separator | `CommonControls.ComboBoxSeparatorFocused` |
| Глиф | `CommonControls.ComboBoxGlyphFocused` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Раскрывающиеся списки и поля со списком полей: Выбор входной текст**  

![Выделение входного текста раскрывающегося списка или списком](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Выделение входного текста раскрывающегося списка или списком  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Выделение | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Табличные элементы управления данными (сетка)  
Табличные элементы управления данными, также называемые элементами управления "Сетка", — это стандартные элементы управления Visual Studio, которые можно использовать для представления больших объемов данных в нескольких столбцах. Стандартные табличные элементы управления данными встречаются в Visual Studio в нескольких местах: в окне инструментов "Список ошибок", в отчетах IntelliTrace, в представлении кучи памяти и т. д. Всегда используйте стандартные табличные элементы управления данными. Однако в некоторых редких случаях доступ к стандартным табличным элементам управления данными может отсутствовать. В таких ситуациях используйте указанные ниже имена токенов для обеспечения согласованности пользовательского интерфейса с другими табличными элементами управления данными в Visual Studio.  

![Элемент управления сетки и табличных данных (красная линия)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Элемент управления сетки или табличных данных (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... для табличной или элементами управления DataGrid. | ... для пользовательского интерфейса, не является элементом управления табличных или сетки. |

#### <a name="column-headers"></a>Заголовки столбцов  
Заголовки столбцов состоят из фона, границы, текста заголовка и необязательного глифа, который обычно используется при сортировке сетки по данному столбцу.  

**Заголовок столбца: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Header.Default` |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Header.Glyph` |
| Border | `Header.SeparatorLine` |

**Заголовок столбца: наведите указатель мыши состояния**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Header.MouseOver` |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Передний план (глиф) | `Header.MouseOverGlyph` |
| Border | `Header.SeparatorLine` |

**Заголовок столбца: нажата состояния**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `CommonControls.CheckBoxBackgroundPressed` |
| Передний план (текст) | `CommonControls.CheckBoxBorderPressed` |
| Передний план (глиф) | `CommonControls.CheckBoxTextPressed` |
| Border | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Элементы представления списка  
 Элементы представления списка состоят из фона и содержимого. Содержимым может быть текст, значок или и то и другое.  

**Элементы представления списка: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Прозрачный |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Border | Нет |

**Элементы представления списка: активное состояние**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `TreeView.SelectedItemActive` |
| Передний план (текст) | `TreeView.SelectedItemActiveText` |
| Border | Нет |

**Элементы представления списка: неактивное состояние**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `TreeView.SelectedItemInactive` |
| Передний план (текст) | `TreeView.SelectedItemInactiveText` |
| Border | Нет |  

### <a name="ui-text"></a>Текст пользовательского интерфейса

#### <a name="instructional-text"></a>Пояснительный текст
Пояснительный текст дает заметного основной объяснение того, что следует сделать на странице диалогового окна или документа.

![Пояснительный текст по умолчанию](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Пояснительный текст по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Дополнительный текст инструкции
На страницах документа с большим количеством текста и элементов управления пояснительный текст использует значение другой цвет. Это помогает показывают, какие сведения о наиболее важных и уменьшают общее плотность элементы пользовательского интерфейса. (См. также под разделом на подсказке.)

![Дополнительный текст инструкции](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Дополнительный текст инструкции

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Текст подсказки
Пояснительный текст отображается в пустой элемент управления, ниже элемента управления или в рабочей области для отображения пользователю, что делать дальше пустой документ. Текст подсказки можно использовать с фон окна или элемента управления.

**Текст подсказки по умолчанию**

![Текст подсказки по умолчанию](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Текст подсказки по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.ControlEditHintText` |

**Требуется указание текста**

![Требуется указание текста](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Требуется указание текста

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.ControlRequiredHintText` |
| Фон | `Environment.ControlRequiredBackground` |

**Текст элемента управления в поле поиска**

> В разделе [окна поиска](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) для других токены цветов, связанных с элементом управления для поиска.

![Текст элемента управления в поле поиска](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Текст элемента управления в поле поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Гиперссылка  
Гиперссылка — это один элемент управления, у которого нет пары переднего плана и фона. Во всех случаях используйте основной цвет гиперссылки, который будет правильно отображаться на темном, сером и белый фон. Если вы не используете токен цвета для элемента управления hyperlink, вы увидите, что по умолчанию системный цвет для «активный», который будет мигать красным. Это означает, что элемент управления не использует неправильный токен цвета среды.  

![Гиперссылка (красная линия)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Гиперссылка (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ..., когда требуется создать пользовательскую гиперссылку. | ... для любого элемента, не гиперссылки. |

**Гиперссылки: состояние по умолчанию**  

![Гиперссылка по умолчанию](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Гиперссылка по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlink` |

**Гиперссылки: состояния наведения мыши**

![Гиперссылка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Гиперссылка при наведении курсора мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlinkHover` |

**Гиперссылки: нажатом состоянии**

![Нажатая гиперссылки](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Нажатая гиперссылки  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlinkPressed` |

**Гиперссылки: отключенном состоянии**

![Отключенные гиперссылки](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Отключенные гиперссылки  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Информационные панели  
Информационные панели служат для предоставления дополнительной информации о данном контексте и всегда отображаются в верхней части окна документа или окна инструментов.  

![Информационная панель (красная линия)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Информационная панель (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... при создании пользовательских информационных панелей. | ... для элементов пользовательского интерфейса, которые не похожи на информационную панель. |

**Информационной панели: состояние по умолчанию**

![Информационная панель по умолчанию](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Информационная панель по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `InfoBar.InfoBarBackground` |
| Передний план (текст) | `InfoBar.InfoBar` |
| Border | `InfoBar.InfoBarBorder` |

**Закрыть информационную панель (&times;) кнопки: состояние по умолчанию**

![По умолчанию закройте информационную панель (&times;) кнопки](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />По умолчанию закройте информационную панель (&times;) кнопки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `InfoBar.CloseButton` |
| Border | `InfoBar.CloseButtonBorder` |
| Глиф | `InfoBar.CloseButtonGlyph` |

**Закрыть информационную панель (&times;) кнопки: наведите указатель мыши состояния**

![Закрыть информационную панель (&times;) кнопка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Закрыть информационную панель (&times;) кнопка при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `InfoBar.CloseButtonHover` |
| Border | `InfoBar.CloseButtonHoverBorder` |
| Глиф | `InfoBar.CloseButtonHoverGlyph` |

**Закрыть информационную панель (&times;) кнопки: активная состояния**

![Нажата закрыть информационную панель (&times;) кнопки](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Нажата закрыть информационную панель (&times;) кнопки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `InfoBar.CloseButtonDown` |
| Border | `InfoBar.CloseButtonDownBorder` |
| Глиф | `InfoBar.CloseButtonDownGlyph` |

**Кнопка гиперссылки информационная панель: состояние по умолчанию**

![Кнопка гиперссылки информационная панель по умолчанию](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Кнопка гиперссылки информационная панель по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `InfoBar.Hyperlink` |

**Кнопка гиперссылки информационная панель: наведите указатель мыши состояния**

![Информационная панель гиперссылки кнопка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Информационная панель гиперссылки кнопка при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseOver`<br />(С подчеркиванием) |

**Кнопка гиперссылки информационная панель: нажата состояния**

![Кнопка гиперссылки нажатая информационная панель](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Кнопка гиперссылки нажатая информационная панель

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseDown`<br />(С подчеркиванием) |

**Гиперссылки встроенная информационная панель (в предложении): состояние по умолчанию**

![Информационная панель Гиперссылка по умолчанию встроенной кнопки](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Информационная панель Гиперссылка по умолчанию встроенной кнопки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `InfoBar.Hyperlink` |

**Гиперссылки встроенная информационная панель (в предложении): наведите указатель мыши состояния**

![Информационная панель встроенной гиперссылки, кнопки при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Информационная панель встроенной гиперссылки, кнопки при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseOver`<br />(С подчеркиванием) |

**Гиперссылки встроенная информационная панель (в предложении): нажата состояния**

![Активная кнопка гиперссылки встроенная информационная панель](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Активная кнопка гиперссылки встроенная информационная панель

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseDown`<br />(С подчеркиванием) |

**Информационная панель кнопок: состояние по умолчанию**

![Кнопка по умолчанию информационной панели](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Кнопка по умолчанию информационной панели

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `InfoBar.Button` |
| Передний план (текст) | `InfoBar.Button` |
| Border | `InfoBar.ButtonBorder` |

**Информационная панель кнопок: наведите указатель мыши состояния**

![Информационная панель Кнопка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Информационная панель Кнопка при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `InfoBar.ButtonMouseOver` |
| Передний план (текст) | `InfoBar.ButtonMouseOver` |
| Border | `InfoBar.ButtonMouseOverBorder` |

**Информационная панель кнопок: нажата состояния**

![Информационная панель нажатой кнопки](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Информационная панель нажатой кнопки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `InfoBar.ButtonMouseDown` |
| Передний план (текст) | `InfoBar.ButtonMouseDown` |
| Border | `InfoBar.ButtonMouseDownBorder` |

**Информационная панель кнопок: в отключенном состоянии**

![Кнопка отключенные информационной панели](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Кнопка отключенные информационной панели

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `InfoBar.ButtonDisabled` |
| Передний план (текст) | `InfoBar.ButtonDisabled` |
| Border | `InfoBar.ButtonDisabledBorder` |

**Информационная панель кнопок: состояние с фокусом ввода**

![Кнопка конкретное информационной панели](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Кнопка конкретное информационной панели

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `InfoBar.ButtonFocus` |
| Передний план (текст) | `InfoBar.ButtonFocus` |
| Border | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Полосы прокрутки  
Полосы прокрутки выглядят средой Visual Studio и не требуется быть включен в тему. Тем не менее может решить, что вы хотите использовать цвета, применяемые в полосах прокрутки, чтобы ваш пользовательский Интерфейс был согласован с этой частью среды Visual Studio.  

![Полоса прокрутки (красная линия)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Полоса прокрутки (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... при создании пользовательского интерфейса, который должен соответствовать полосы прокрутки Visual Studio. | ... для ничего не должны всегда соответствовать пользовательского интерфейса "полоса прокрутки". |

**Полоса прокрутки: состояние по умолчанию**  

![Полоса прокрутки по умолчанию](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Полоса прокрутки по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Полоса прокрутки | `Environment.ScrollBarBackground` |
| Передний план (бегунок) | `Environment.ScrollBarThumbBackground` |

**Полоса прокрутки: наведите указатель мыши состояния**

![Полосы прокрутки при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Полоса прокрутки при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Полоса прокрутки | `Environment.ScrollBarBackground` |
| Передний план (бегунок) | `Environment.ScrollBarThumbMouseOverBackground` |

*Полоса прокрутки: нажата состояния**

![Активная полоса прокрутки](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Активная полоса прокрутки  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Полоса прокрутки | `Environment.ScrollBarBackground` |
| Передний план (бегунок) | `Environment.ScrollBarThumbPressedBackground` |

**Стрелка "полоса прокрутки": состояние по умолчанию**  

![Стрелки полосы прокрутки по умолчанию](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Стрелки полосы прокрутки по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ScrollBarArrowBackground`<br />(Значение совпадает с цветом полосы прокрутки). |
| Передний план (глиф) | `Environment.ScrollBarArrowGlyph` |

**Стрелка "полоса прокрутки": наведите указатель мыши состояния**

![Стрелки полосы прокрутки при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Стрелки полосы прокрутки при наведении курсора мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ScrollBarArrowMouseOverBackground`<br />(Значение совпадает с цветом полосы прокрутки). |
| Передний план (глиф) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Стрелка "полоса прокрутки": нажата состояния**  

![При нажатии стрелки полосы прокрутки](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />При нажатии стрелки полосы прокрутки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ScrollBarArrowPressedBackground`<br />(Значение совпадает с цветом полосы прокрутки). |
| Передний план (глиф) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="BKMK_SearchBoxes"></a>Поля поиска  
По возможности используйте стандартный элемент управления поиском, предоставляемый средой Visual Studio. Цвета поля поиска находятся в категории SearchControl в файле **ShellColors.pkgdef** , который содержит имена токенов для поля ввода, управляющей кнопки, кнопки раскрывающегося списка и раскрывающегося меню.  

Поле поиска может находиться в одном из нескольких состояний. Некоторые из них взаимоисключающие.  

-   "С фокусом ввода" или "без фокуса ввода" указывает на то, находится ли курсор в текстовом поле.  

-   "Активно" или "неактивно" указывает на то, ввел ли пользователь запрос в текстовом поле.  

-   "При наведении указателя" означает, что пользователь навел указатель мыши на поле поиска (это состояние переопределяет все остальные).  

-   "Отключено" означает, что функция поиска в текущем контексте отключена.  

![Поле поиска (красная линия)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Поле поиска (красная линия)  

| Используйте: | Не используйте: |
| --- | --- |
| ... при разработке пользовательского поля поиска. | ... для любого элемента, не входящий в поле поиска. |
| | ... для параметров, которые вы не должны всегда соответствовать поиск поля пользовательского интерфейса. |

**Поле ввода окна поиска с фокусом ввода**

![Поле ввода окна поиска с фокусом ввода](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Поле ввода окна поиска с фокусом ввода  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `SearchControl.FocusedBackground` |
| Передний план (текст) | `SearchControl.FocusedBackground` |
| Border | `SearchControl.FocusedBorder` |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Поле ввода окна поиска без фокуса ввода, active**

![Поле ввода окна поиска без фокуса ввода](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Поле ввода окна поиска без фокуса ввода, active

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `SearchControl.SearchActiveBackground` |
| Передний план (текст) | `SearchControl.SearchActiveBackground` |
| Border | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Поле ввода окна поиска без фокуса ввода, неактивные**

![Поле ввода окна поиска без фокуса ввода, неактивные](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Поле ввода окна поиска без фокуса ввода, неактивные  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `SearchControl.Unfocused` |
| Передний план (текст) | `SearchControl.Unfocused` |
| Border | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Поле ввода окна поиска выделенный (текст)**

![Поле ввода окна поиска выделенный](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Поле ввода окна поиска выделенный

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `SearchControl.Selection` |
| Передний план (текст) | `SearchControl.FocusedBackground` |
| Border | Нет |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Поле ввода окна поиска отключено**

![Поле ввода окна поиска отключено](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Поле ввода окна поиска отключено

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `SearchControl.Disabled` |
| Передний план (текст) | `SearchControl.Disabled` |
| Border | `SearchControl.DisabledBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Кнопка поиска с фокусом ввода**

![Кнопка поиска с фокусом ввода](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Кнопка поиска с фокусом ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Нет |
| Передний план (глиф поиска) | `SearchControl.SearchGlyph` |
| Передний план (глиф остановки) | `SearchControl.StopGlyph` |
| Передний план (глиф очистки) | `SearchControl.ClearGlyph` |
| Border | Н/Д |

**Кнопка поиска без фокуса ввода**  

![Кнопка поиска без фокуса ввода](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Кнопка поиска без фокуса ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Н/Д |
| Передний план (глиф поиска) | `SearchControl.SearchGlyph` |
| Передний план (глиф остановки) | `SearchControl.StopGlyph` |
| Передний план (глиф очистки) | `SearchControl.ClearGlyph` |
| Border | Н/Д |

**Нажата кнопка поиска**

![Нажата кнопка поиска](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Нажата кнопка поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `SearchControl.ActionButtonMouseDown` |
| Передний план (глиф) | `SearchControl.ActionButtonMouseDownGlyph` |
| Border | `SearchControl.ActionButtonMouseDownBorder` |

**Кнопка поиска отключено**

![Неактивная кнопка поиска](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Кнопка поиска отключено

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Нет |
| Передний план (глиф) | `SearchControl.ActionButtonDisabledGlyph` |
| Border | Нет |

**Кнопка раскрывающегося списка поиска с фокусом ввода**

![Кнопка раскрывающегося списка поиска с фокусом ввода](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Кнопка раскрывающегося списка поиска с фокусом ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `SearchControl.FocusedDropDownButton` |
| Передний план (глиф) | `SearchControl.FocusedDropDownButtonGlyph` |
| Border | `SearchControl.FocusedDropDownButtonBorder` |

**Кнопка раскрывающегося списка поиска без фокуса ввода**

![Кнопка раскрывающегося списка поиска без фокуса ввода](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Кнопка раскрывающегося списка поиска без фокуса ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `SearchControl.UnfocusedDropDownButton` |
| Передний план (глиф) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Border | `SearchControl.UnfocusedDropDownButtonBorder` |

**Активная кнопка раскрывающегося списка поиска**

![Активная кнопка раскрывающегося списка поиска](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Активная кнопка раскрывающегося списка поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `SearchControl.MouseDownDropDownButton` |
| Передний план (глиф) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Border | `SearchControl.MouseDownDropDownButtonBorder` |

**Кнопка раскрывающегося списка поиска отключено**

![Кнопка раскрывающегося списка поиска отключено](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Кнопка раскрывающегося списка поиска отключено

| Элемент | Имя токена: Category.color |
| --- | --- |  
| Фон | Нет |
| Передний план (глиф) | `SearchControl.DisabledDownButtonGlyph` |
| Border | Нет |

#### <a name="search-drop-down-lists"></a>Раскрывающиеся списки поиска  
Раскрывающееся меню поля поиска может быть немного более сложными, чем другие раскрывающиеся меню в Visual Studio. «Предлагаемые запросы поиска» и «параметры поиска» разделы могут использоваться отдельно или вместе в меню, и каждый из них имеет цвет отдельно. Если имеются оба этих раздела, они разделяются линией, а все раскрывающееся меню окружено границей.  

![Поиск раскрывающегося списка (красная линия)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Поиск раскрывающегося списка (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... при создании пользовательского раскрывающегося списка поиска. | ... для раскрывающихся списков, которые используются в других контекстах. |
| ... правильные имена токенов для соответствующих компонентов списка. | в сочетании любой фона и цвета переднего плана, отличном от определенных. |

**Элементы раскрывающегося списка поиска**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Border | `SearchControl.PopupBorder` |
| Separator | `SearchControl.PopupSectionHeaderSeparator` |
| Тень | `Environment.DropShadowBackground` |

**Предлагаемый поиск: состояние по умолчанию**

![По умолчанию предлагаемые запросы поиска](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />По умолчанию предлагаемые запросы поиска  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `SearchControl.PopupItemText` |

**Предлагаемый поиск: наведите указатель мыши состояния**

![Предлагаемые запросы поиска при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Предлагаемые запросы поиска при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `SearchControl.PopupMouseOverItemText` |
| Border | `SearchControl.PopupControlMouseOverBorder` |

**Параметры поиска: состояние по умолчанию**

![Флажок поиска](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />По умолчанию параметры поиска (флажок)  

![Параметры поиска](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Параметры поиска по умолчанию (ссылка)  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст флажка) | `SearchControl.PopupCheckboxText` |
| Передний план (текст ссылки) | `SearchControl.PopupButtonText` |
| Фон заголовка | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст заголовка) | `SearchControl.PopupSectionHeaderText` |

**Параметры поиска: наведите указатель мыши состояния**

![Параметры поиска (флажок) при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Параметры поиска (флажок) при наведении курсора мыши  

![Параметры поиска (ссылка) при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Параметры поиска (ссылка) при наведении курсора мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст флажка) | `SearchControl.PopupCheckboxMouseDownText` |
| Передний план (текст ссылки) | `SearchControl.PopupButtonMouseDownText` |
| Border | `SearchControl.PopupControlMouseOverBorder` |

**Параметры поиска: нажата состояния**  

![Нажата параметры поиска (флажок)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Нажата параметры поиска (флажок)   

![Нажата параметры поиска (ссылка)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Нажата параметры поиска (ссылка)  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон флажка | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст флажка) | `SearchControl.PopupCheckboxMouseDownText` |
| Фон ссылки | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст ссылки) | `SearchControl.PopupButtonMouseDownText` |

###  <a name="BKMK_TreeView"></a>Представления в виде дерева  
Некоторых окнах инструментов, включая обозреватель решений, обозреватель серверов и представление классов, реализована иерархическая организационная схема, цвета которой определяются названиями цветов в `TreeView` категории. Все элементы в иерархическом представлении имеют цвета фона и текста. Элементы с вложенными дочерними элементами также имеют глифы, которые указывают на то, является ли элемент свернутым или развернутым.  

![Представление в виде дерева (красная линия)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Представление в виде дерева (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... в любом необходимо реализовать иерархическое представление. | ... для любого элемента, не аналогично представление в виде дерева. |
| | в сочетании любой фона и цвета переднего плана, отличном от определенных. |

**Элемент дерева: состояние по умолчанию**

![По умолчанию элемент дерева](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />По умолчанию элемент дерева

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `TreeView.Background` |
| Передний план (текст) | `TreeView.Background` |
| Передний план (глиф) | `TreeView.Glyph` |
| Border | Нет |

**Элемент дерева: наведите указатель мыши состояния**

![Элемент дерева при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Элемент дерева при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `TreeView.Background` |  
| Передний план (текст) | `TreeView.Background` |
| Передний план (глиф) | `TreeView.GlyphMouseOver` |
| Border | Нет |

**Элемент дерева: перетащите на состояние**

![Перетащите элемент дерева на](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Перетащите элемент дерева на  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `TreeView.DragOverItem` |
| Передний план (текст) | `TreeView.DragOverItem` |
| Передний план (глиф) | `TreeView.DragOverItemGlyph` |
| Border | Нет |

**Элемент дерева: выбран, состояние с фокусом ввода**

![Элемент дерева выбранного и имеющего фокус](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Элемент дерева выбранного и имеющего фокус

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `TreeView.SelectedItemActive` |
| Передний план (текст) | `TreeView.SelectedItemActive` |
| Передний план (глиф) | `TreeView.SelectedItemActiveGlyph` |
| Border | `TreeView.FocusVisualBorder` |

**Элемент дерева: состояние выбранного, без фокуса ввода**  

![Элемент дерева выбранного и без фокуса ввода](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Элемент дерева выбранного и без фокуса ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `TreeView.SelectedItemInactive` |
| Передний план (текст) | `TreeView.SelectedItemInactive` |
| Передний план (глиф) | `TreeView.SelectedItemInactiveGlyph` |
| Border | Нет |

**Элемент дерева: указателем мыши, выбрать и состояния с фокусом ввода**

![Элемент выбранные и имеющего фокус дерева при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Элемент выбранные и имеющего фокус дерева при наведении курсора мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `TreeView.SelectedItemActive` |
| Передний план (текст) | `TreeView.SelectedItemActive` |
| Передний план (глиф) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Border | `TreeView.FocusVisualBorder` |

**Элемент дерева: состояние изменившегося выбранного и без фокуса ввода**

![Элемент дерева выбранной и без фокуса ввода при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Элемент дерева выбранного и без фокуса ввода при наведении курсора мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `TreeView.SelectedItemInactive` |
| Передний план (текст) | `TreeView.SelectedItemInactive` |
| Передний план (глиф) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Border | Нет |

## <a name="shell-appearance"></a>Вид оболочки

### <a name="background"></a>Фон  
Фон среды состоит из двух слоев. Нижний слой представляет собой сплошной цвет, который охватывает всю интегрированную среду разработки. Верхний слой используется под командной полкой и между каналами автоматического скрытия окон инструментов по левому и правому краям интегрированной среды разработки. Слои фона верхней и нижней устанавливаются в светлой и темной темах одинаковый цвет.  

![Фоновой оболочки Visual Studio (красная линия)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Фоновой оболочки Visual Studio (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... для места, где необходимо соответствовать фону среды Visual Studio. | … как заливки для областей, которые не являются фоновыми. |
| | ... в качестве фона для размещения на элементы переднего плана. |

**Вид оболочки нижнего уровня**

| Элемент | Имя токена: Category.color |
| --- | --- |  
| Фон | `Environment.EnvironmentBackground` |

**Вид оболочки верхний слой**

> Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.

| Элемент | Имя токена: Category.color |
| --- | --- |  
| Фон | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |  

### <a name="command-shelf"></a>Командная полка  
Для фона командной полки используются два набора имен токенов: один для области размещения строки меню, а другой — для области размещения панелей команд. Отдельные группы на панели команд имеют собственные значения цветов фона, которые более подробно рассматриваются в разделе, посвященном панели команд. Цвета текста строки меню и панели команд рассматриваются в разделах, посвященных меню и панели команд.  

![Командная Полка Visual Studio (красная линия)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Командная Полка Visual Studio (красная линия)  

| Используйте: | Не используйте: |
| --- | --- |
| ... для областей, где размещаются меню или панели инструментов. | ... для областей, которые не являются аналогично командная Полка. |
|... with комбинация имя токена правильный фона и цвета переднего плана. | |

**Строка меню командной полки**

> Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.

| Элемент | Имя токена: Category.color |
| --- | --- |  
| Фон | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

** Командной полки командной панели **

> Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.

| Элемент | Имя токена: Category.color |
| --- | --- |  
| Фон | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Конструктор манифеста  
Конструктор манифеста призван упростить редактирование файла манифеста в проектах Windows 8 и Windows Phone 8. Хотя общего готового шаблона нет, рекомендуется обеспечивать соответствие макету и цветам вкладок ориентации и навигации, а также общей структуре. Дополнительные сведения о макете см. в разделе [макета для Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  

![Конструктор манифеста (красная линия)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Конструктор манифеста (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... для конструкторов, которые похожи на конструктор манифеста. | ... При наличии более чем шести вкладок. |
| ... вместо использования стандартных элементов управления вкладки в верхней части редактора в документе хорошо. | ... для пользовательского интерфейса, не структурирован от конструктора манифеста. |

**Выбранная вкладка манифеста конструктора: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `ManifestDesigner.TabActive` |
| Border | Нет |

**Панель выбранные описания манифеста конструктора: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `ManifestDesigner.DescriptionPane` |

**Страница выбранного содержимого манифеста конструктора: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `ManifestDesigner.Background` |
| Текст подсказки для диалогового окна | `ManifestDesigner.WatermarkText`<br />(Это имя токена не соответствует его функции.) |

**Вкладка "манифест конструктор": не выбрано состояние**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `ManifestDesigner.Tab.Inactive` |

**Вкладка "манифест конструктор": наведите указатель мыши состояния**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Структура команд  

###  <a name="BKMK_CommandMenus"></a>Меню  
Меню может произойти в нескольких местах в среде Visual Studio: в главном меню, внедренных в документов или окно инструментов или щелкните правой кнопкой мыши в различных местах в Интегрированной среде разработки. Реализация меню, связанных с другими элементами пользовательского интерфейса, рассматривается в разделах, посвященных соответствующим элементам. Всегда используйте стандартную реализацию меню, предоставляемую средой Visual Studio. Однако в некоторых редких случаях доступ к стандартным меню Visual Studio может отсутствовать. В таких ситуациях используйте указанные ниже имена токенов для обеспечения согласованности пользовательского интерфейса с другими меню в Visual Studio.  

![Меню Visual Studio (красная линия)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Меню Visual Studio (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... При необходимости создать пользовательское меню.| ... только цветом фона. Всегда используйте определенное сочетание цвета фона и цвета переднего плана. |
| ... При наличии новый компонент пользовательского интерфейса, который должен соответствовать меню Visual Studio.| |

#### <a name="menu-titles"></a>Заголовков меню  
Заголовок меню состоит из фона, границы и текста заголовка, а также необязательного глифа (обычно если меню находится на панели команд).  

![Заголовок меню (красная линия)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Заголовок меню (красная линия)  

| Используйте: | Не используйте: |
| --- | --- |
| ... каждый раз, когда вы создаете пользовательского заголовка меню. | ... для параметров, которые не должны всегда соответствовать заголовку меню. |
| | в сочетании любой фона и цвета переднего плана, отличном от определенных. |

**Заголовок меню: состояние по умолчанию**

![Заголовок меню по умолчанию](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Заголовок меню по умолчанию

![По умолчанию заголовок меню с глифом](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />По умолчанию заголовок меню с глифом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Нет |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Environment.CommandBarMenuGlyph` |
| Border | Нет |

**Заголовок меню: наведите указатель мыши состояния**  

![Заголовок меню при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Заголовок меню при наведении курсора мыши  

![Заголовок меню с глифом при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Заголовок меню с глифом при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Передний план (глиф) | `Environment.CommandBarMenuMouseOverGlyph` |  
| Border | `Environment.CommandBarBorder` |

**Заголовок меню: нажата состояния**  

![Заголовок меню в нажатом состоянии](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Заголовок меню в нажатом состоянии

![При нажатии заголовка меню с глифом](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />При нажатии заголовка меню с глифом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Environment.CommandBarMenuMouseDownGlyph` |
| Border | `Environment.CommandBarMenuBorder`<br />(Только левую, верхнюю и правую части.) |  

**Заголовок меню: в отключенном состоянии**  

![Заголовок отключенного меню с глифом](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Заголовок отключенного меню с глифом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Нет |
| Передний план (текст) | `Environment.CommandBarTextInactive` |
| Передний план (глиф) | `Environment.CommandBarTextInactive` |
| Border | Нет |

#### <a name="menu-items"></a>Пункты меню
Отдельный пункт меню состоит из текста и необязательных значка, флажка или глифа подменю. Его цвета фона и текста меняются при наведении указателя. Этот токен цвета представляет собой пару, состоящую из цвета фона и цвета переднего плана.  

![Красная линия пунктов меню](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303 009_MenuItemRedline")  

| Используйте: | Не используйте:  |
|---|---|
| ... для любого раскрывающегося списка, запускаемый из строки меню или панели команд. | ... для раскрывающегося списка в другом контексте. |
| | в сочетании любой фона и цвета переднего плана, отличном от определенных. |

**Пункты меню: состояние по умолчанию**

![Элементы меню по умолчанию](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Элементы меню по умолчанию  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф подменю) | `Environment.CommandBarMenuSubmenuGlyph` |
| Border | `Environment.CommandBarMenuBorder` |
| Фон канала значка | `Environment.CommandBarMenuIconBackground` |
| Separator | `Environment.CommandBarMenuSeparator` |
| Тень | `Environment.DropShadowBackground` |

**Пункты меню: отмечена и выбрана состояний**  

![Меню с установленным флажком](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Меню проверенного элемента

![Выбранное меню](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Выбранного пункта меню    

| Элемент | Имя токена: Category.color |
| --- | --- |
| Флажок | `Environment.CommandBarCheckBox` |  
| Фон флажка | `Environment.CommandBarSelectedIcon` |  
| Фон значка | `Environment.CommandBarSelected` |
| Граница значка | `Environment.CommandBarSelectedBorder` |

**Пункты меню: наведите указатель мыши состояния**  

![Меню при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Пункт меню при наведении курсора мыши

![Меню при наведении указателя мыши проверяется](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Проверка элемента меню при наведении курсора мыши

![Меню при наведении указателя мыши выбран](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Выбранный пункт меню при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.CommandBarMenuItemMouseOver` |
| Передний план (текст) | `Environment.CommandBarMenuItemMouseOver` |
| Передний план (глиф подменю) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Флажок | `Environment.CommandBarCheckBoxMouseOver` |
| Фон флажка | `Environment.CommandBarHoverOverSelectedIcon` |
| Фон значка | `Environment.CommandBarHoverOverSelected` |
| Граница значка | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Пункты меню: в отключенном состоянии**  

![Неактивное меню](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Отключенный элемент меню

![Проверка меню отключена](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Отключенный элемент меню с галочкой

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.CommandBarTextInactive` |
| Передний план (глиф подменю) | `Environment.CommandBarMenuSubmenuGlyph` |
| Флажок | `Environment.CommandBarCheckBoxDisabled` |
| Фон флажка | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Панели команд  
Панель команд может появляться в нескольких местах в СРЕДЕ Visual Studio, прежде всего командная полка и инструментов или окна документа.  

Как правило, следует всегда использовать стандартную реализацию панели команд, предоставляемую средой Visual Studio. Использование стандартного механизма обеспечивает правильное отображение визуальных элементов и согласованное поведение интерактивных элементов и других элементов управления панели команд Visual Studio. Однако если вам необходимо создать собственную панель команд, следует правильно оформить ее с помощью указанных ниже имен токенов.  

![Красная линия командной строки](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Панель команд (красная линия)  

![Красная линия кнопки переполнения](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Кнопка переполнения (красная линия)  

| Используйте: | Не используйте: |
| --- | --- |
| ... в местах, где требуется внедренная команда панели, но не смогут использовать стандартную реализацию панели команд Visual Studio. | ... для элементов пользовательского интерфейса, которые не похоже на панель команд. |
| | ... для компонентов панели команд, отличных от тех, для которых определены имена токенов. |

#### <a name="command-bar-groups"></a>Группы панель команд  
Группа панели команд состоит из связанного набора элементов управления панели команд и может содержать любое количество кнопок, разворачивающихся кнопок, раскрывающихся меню, полей со списками или меню. Цвета этих элементов управления определяются отдельными именами токенов, которые рассматриваются в других частях этого руководства. Разделительная линия служит для разделения группы на панели команд в связанные подгруппы.  

![Красная линия группа панели команд](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Группа панели команд (красная линия)

| Используйте: | Не используйте: |
| --- | --- |  
| ... в местах, где требуется внедренная команда панели, но не смогут использовать стандартную реализацию панели команд Visual Studio. | ... для элементов пользовательского интерфейса, которые не похоже на панель команд. |
| | ... для компонентов панели команд, отличных от тех, для которых определены имена токенов. |

**Группа панели команд: состояние по умолчанию**  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.CommandBarGradientBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Border | `Environment.CommandBarToolBarBorder` |
| Маркер перетаскивания | `Environment.CommandBarDragHandle` |
| Separator | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Значки команд  
![Красная линия значка команды](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Значок команды (красная линия)  

![Красная линия значка команды с текстом](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Значок команды с текстом (красная линия)  

| Используйте: | Не используйте: |
| --- | --- |
| ... для кнопок, которые будут размещаться на панели команд. | ... для элементов управления, имеющих собственные имена токенов. |
| | в сочетании любой фона и цвета переднего плана, отличном от определенных. |

**Значок команды: состояние по умолчанию**  

![Значок команды по умолчанию](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Значок команды по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Н/Д (наследуется от фона панели команд) |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Border | Н/Д |

**Значок команды: состояние, выбранные по умолчанию**

![По умолчанию, значок выбранной команды](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />По умолчанию, значок выбранной команды  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.CommandBarSelected` |
| Передний план (текст) | `Environment.CommandBarTextSelected` |
| Border | `Environment.CommandBarSelectedBorder` |

**Значок команды: состояния наведения или фокуса**  

![Значок команды при наведении указателя мыши или фокуса](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Значок команды при наведении указателя мыши или фокуса

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Border | `Environment.CommandBarBorder` |

**Значок команды: при наведении указателя мыши или фокус состояний, выбранных**

![Значок выбранной команды при наведении указателя мыши или фокуса](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Значок выбранной команды при наведении указателя мыши или фокуса

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.CommandBarHoverOverSelected` |
| Передний план (текст) | `Environment.CommandBarTextHoverOverSelected` |
| Border | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Значок команды: нажата состояния**  

![Активный значок команды](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Активный значок команды

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.CommandBarTextMouseDown` |
| Border | `Environment.CommandBarBorder` |

**Значок команды: в отключенном состоянии**  

![Неактивный значок команды](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Неактивный значок команды

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Н/Д (наследуется от фона панели команд) |
| Передний план (текст) | `Environment.CommandBarTextInactive` |
| Border | Н/Д |

####  <a name="BKMK_CommandComboBox"></a>Поля со списком командной строки

> [!IMPORTANT]
> Поле со списком похоже на раскрывающийся список, но включает область для ввода и редактирования текста. Если раскрывающийся список не включает область для редактирования текста, используйте токены цветов для [командной строке раскрывающихся списков](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).  

![Красная линия командной строки со списком](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Поле со списком командной строки (красная линия)  

| Используйте: | Не используйте: |
| --- | --- |
| ... при построении пользовательского поля со списком. | ... для любого элемента вы не должны всегда соответствовать команда Интерфейс панели. |
| ... при создании элемент управления командной строки, которая похожа на поле со списком. | ... Если имеется доступ к оформленным поле со списком. |

**Команда панели поле поля со списком ввода: состояние по умолчанию**

![Команда панели поле поля со списком ввода](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Команда панели поле поля со списком ввода  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ComboBoxBackground` |
| Передний план (текст) | `Environment.ComboBoxText` |
| Border | `Environment.ComboBoxBorder` |
| Separator | Без разделителя |

**Кнопка раскрывающегося списка командной строки: состояние по умолчанию**  

![Поле со списком поле drop &#45; вниз кнопки](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Кнопка раскрывающегося списка командной строки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Н/Д (наследуется от фона панели команд) |
| Передний план (глиф) | `Environment.ComboBoxGlyph` |

**Раскрывающегося списка командной строки: состояние по умолчанию**

![Раскрывающегося списка командной строки](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Раскрывающегося списка командной строки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ComboBoxPopupBackgroundBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.ComboBoxItemText` |
| Border | `Environment.ComboBoxPopupBorder` |

**Команда панели поле поля со списком ввода: наведите указатель мыши состояния**  

![Команда панели поле ввода поля со списком при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Команда панели поле ввода поля со списком при наведении курсора мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.ComboBoxMouseOverText` |
| Border | `Environment.ComboBoxMouseOverBorder` |
| Separator | `Environment.ComboBoxMouseOverSeparator` |

 **Кнопка раскрывающегося списка командной строки: наведите указатель мыши состояния**  

![Кнопка раскрывающегося списка командной строки при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Кнопка раскрывающегося списка командной строки при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ComboBoxButtonMouseOverBackground` |
| Передний план (глиф) | `Environment.ComboBoxMouseOverGlyph` |

**Раскрывающегося списка командной строки: наведите указатель мыши состояния**

 ![Команда панели раскрывающегося списка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Команда панели раскрывающегося списка при наведении курсора мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон (пункт меню) | `Environment.ComboBoxItemMouseOverBackground` |
| Передний план (текст) | `Environment.ComboBoxItemMouseOverText` |
| Граница (пункт меню) | `Environment.ComboBoxItemMouseOverBorder` |

 **Команда панели поле поля со списком ввода: состояние с фокусом ввода**  

![Команда панели поле поля со списком ввода с фокусом ввода](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Команда панели поле поля со списком ввода с фокусом ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ComboBoxFocusedBackground` |
| Передний план (текст) | `Environment.ComboBoxFocusedText` |
| Border | `Environment.ComboBoxFocusedBorder` |
| Separator | `Environment.ComboBoxFocusedButtonSeparator` |

**Кнопка раскрывающегося списка командной строки: состояние с фокусом ввода**  

![Конкретное командной панели кнопку раскрывающегося списка](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Конкретное командной панели кнопку раскрывающегося списка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ComboBoxFocusedButtonBackground` |
| Передний план (глиф) | `Environment.ComboBoxFocusedGlyph` |

 **Команда панели поле поля со списком ввода: нажата состояния**  

![Нажата командной строке поле поля со списком ввода](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Нажата командной строке поле поля со списком ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ComboBoxMouseDownBackground` |
| Передний план (текст) | `Environment.ComboBoxMouseDownText` |
| Border | `Environment.ComboBoxMouseDownBorder` |
| Separator | `Environment.ComboBoxMouseDownSeparator` |

**Кнопка раскрывающегося списка командной строки: нажата состояния**

![Активная кнопка раскрывающегося списка на панели команд](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Активная кнопка раскрывающегося списка на панели команд  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ComboBoxButtonMouseDownBackground` |
| Передний план (глиф) | `Environment.ComboBoxMouseDownGlyph` |

**Команда панели поле поля со списком ввода: в отключенном состоянии**  

![Отключенные панели поле ввода поля со списком команд](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Отключенные панели поле ввода поля со списком команд  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ComboBoxDisabledBackground` |
| Передний план (текст) | `Environment.ComboBoxDisabledText` |
| Border | `Environment.ComboBoxDisabledBorder` |
| Separator | Без разделителя |

**Кнопка раскрывающегося списка командной строки: в отключенном состоянии**  

![Отключенной командной панели кнопку раскрывающегося списка](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Отключенной командной панели кнопку раскрывающегося списка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Нет |
| Передний план (глиф) | `Environment.ComboBoxDisabledGlyph` |

####  <a name="BKMK_CommandDropDown"></a>Раскрывающийся список командной строки

> [!IMPORTANT]
>  Раскрывающийся список похож на поле со списком, но не имеет области для ввода и редактирования текста. Если раскрывающийся список включает область для редактирования текста, используйте токены цветов для [командной строке поля со списком](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).  

![Команда панели раскрывающегося списка (красная линия)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Команда панели раскрывающегося списка (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... при создании пользовательского раскрывающегося списка элементов управления. | ... для любого элемента, отличных от раскрывающегося списка. |
| | ... для поля со списком и разворачивающиеся кнопки. |   

**Поле выбора раскрывающегося списка командной строки: состояние по умолчанию**  

![Поле выбора раскрывающегося списка по умолчанию командной строки](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Поле выбора раскрывающегося списка по умолчанию командной строки  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.DropDownBackground` |
| Передний план (текст) | `DropDownText` |
| Border | `DropDownBorder` |
| Separator | Без разделителя |

**Кнопка раскрывающегося списка командной строки: состояние по умолчанию**

![Кнопка раскрывающегося списка по умолчанию командной строки](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Кнопка раскрывающегося списка по умолчанию командной строки  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Нет |
| Передний план (глиф) | `Environment.DropDownGlyph` |

**Раскрывающегося списка командной строки: состояние по умолчанию**

![По умолчанию команда панель раскрывающегося списка](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />По умолчанию команда панель раскрывающегося списка  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.DropDownPopupBackgroundBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.ComboBoxItemText` |
| Border | `Environment.DropDownPopupBorder` |
| Тень | `Environment.DropShadowBackground` |

**Поле выбора раскрывающегося списка командной строки: наведите указатель мыши состояния**  

![Поле выбора раскрывающегося списка панели команды при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Поле выбора раскрывающегося списка панели команды при наведении курсора мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.DropDownMouseOverBackgroundBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.DropDownMouseOverText` |
| Border | `Environment.DropDownMouseOverBorder` |
| Separator | `Environment.DropDownButtonMouseOverSeparator` |

**Кнопка раскрывающегося списка командной строки: наведите указатель мыши состояния**  

![Кнопка раскрывающегося списка командной строки при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Кнопка раскрывающегося списка командной строки при наведении курсора мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.DropDownButtonMouseOverBackground` |
| Передний план (глиф) | `Environment.DropDownMouseOverGlyph` |

**Раскрывающегося списка командной строки: наведите указатель мыши состояния**  

![Команда панели раскрывающегося списка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Команда панели раскрывающегося списка при наведении курсора мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон (пункт меню) | `Environment.ComboBoxItemMouseOverBackground` |
| Передний план (текст) | `Environment.ComboBoxItemMouseOverText` |
| Граница (пункт меню) | `Environment.ComboBoxItemMouseOverBorder` |

 **Поле выбора раскрывающегося списка командной строки: нажата состояния**  

![DROP &#45; вниз поле выбора нажата](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Нажата командной строке поле выбора раскрывающегося списка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.DropDownMouseDownBackground` |
| Передний план (текст) | `Environment.DropDownMouseDownText` |
| Border | `Environment.DropDownMouseDownBorder` |
| Separator | `Environment.DropDownButtonMouseDownSeparator` |

**Кнопка раскрывающегося списка командной строки: нажата состояния**

![Активная кнопка раскрывающегося списка на панели команд](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Активная кнопка раскрывающегося списка на панели команд  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.DropDownButtonMouseDownBackground` |
| Передний план (глиф) | `Environment.DropDownMouseDownGlyph` |

**Поле выбора раскрывающегося списка командной строки: в отключенном состоянии**  

![Отключенной командной строке поле выбора раскрывающегося списка](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Отключенной командной строке поле выбора раскрывающегося списка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.DropDownDisabledBackground` |
| Передний план (текст) | `Environment.DropDownDisabledText` |
| Border | `Environment.DropDownDisabledBorder` |
| Separator | Без разделителя |

**Кнопка раскрывающегося списка командной строки: в отключенном состоянии**

![Отключенной командной панели кнопку раскрывающегося списка](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Отключенной командной панели кнопку раскрывающегося списка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Н/Д |
| Передний план (глиф) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Панель команд разворачивающиеся кнопки
Для разворачивающихся кнопок используются многие имена токенов, определенные для других элементов управления панели команд, таких как кнопки, меню и текст панели команд. Все необходимые имена токенов для действий и кнопок раскрывающихся списков приводятся здесь еще раз для удобства. Раскрывающийся список списки разворачивающихся кнопок являются реализацией [панели меню команд](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).  

![Красная линия разворачивающейся кнопки](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Панель команд Разворачивающаяся кнопка (красная линия)  

| Используйте: | Не используйте: |
| --- | --- |
| ... при создании пользовательской разворачивающейся кнопки. | ... для других видов кнопок. |
| | в сочетании любой фона и цвета переднего плана, отличном от определенных. |

**Панель команд Разворачивающаяся кнопка: состояние по умолчанию**  

![По умолчанию панель команд Разворачивающаяся кнопка](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />По умолчанию панель команд Разворачивающаяся кнопка  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Нет |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Environment.CommandBarSplitButtonGlyph` |
| Border | Н/Д |
| Separator | Н/Д |

**Панель команд Разворачивающаяся кнопка: наведите указатель мыши состояния**  

![Панель команд Разворачивающаяся кнопка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Панель команд Разворачивающаяся кнопка при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Передний план (глиф) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Border | `Environment.CommandBarBorder` |
| Separator | `Environment.CommandBarSplitButtonSeparator` |

**Панель команд Разворачивающаяся кнопка: нажата состояния**  

![Панель команд нажатой Разворачивающаяся кнопка](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Панель команд нажатой Разворачивающаяся кнопка  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.CommandBarTextMouseDown` |
| Передний план (глиф) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Border | `Environment.CommandBarBorder` |
| Separator | Н/Д |

**Панель команд Разворачивающаяся кнопка: в отключенном состоянии**

![Кнопка разделения отключенной командной строки](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Кнопка разделения отключенной командной строки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Н/Д |
| Передний план (текст) | `Environment.ComboBoxItemTextInactive` |
| Передний план (глиф) | `Environment.CommandBarTextInactive` |
| Border | Н/Д |
| Separator | Н/Д |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Команда «Дополнительно» и «Переполнение» на панели кнопок  
Кнопка "Дополнительно" используется, если группа панели команд может настраиваться путем добавления или удаления связанных кнопок. Кнопка "Переполнение" появляется, если панель команд усекается из-за отсутствия места по горизонтали. При ее нажатии открывается меню, содержащее кнопки, которые не поместились на панели команд. Цвета этих двух кнопок определяются одним и тем же набором имен токенов.  

![Кнопка «Дополнительные параметры» на панели команд (красная линия)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Кнопка «Дополнительные параметры» на панели команд (красная линия)  

| Используйте: | Не используйте: |
| --- | --- |
| ... для пользовательских «Дополнительно» и «Переполнение» кнопок. | ... для кнопок, которые не имеют аналогичные функциональные возможности для «Дополнительно» или кнопку «Переполнение». |

**«Дополнительно» и «Переполнение» кнопок на панели команд: состояние по умолчанию**  

![По умолчанию панели команд кнопку «Дополнительные параметры»](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />По умолчанию панели команд кнопку «Дополнительные параметры»

![По умолчанию кнопки «Переполнение» командной строки](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />По умолчанию кнопки «Переполнение» командной строки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.CommandBarOptionsBackground` |
| Передний план (глиф) | `Environment.CommandBarOptionsGlyph` |

**«Дополнительно» и «Переполнение» кнопок на панели команд: наведите указатель мыши состояния**

![Команда панели кнопку «Дополнительные параметры» при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Команда панели кнопку «Дополнительные параметры» при наведении курсора мыши  

![Кнопка «Переполнение» команды панели при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Кнопка «Переполнение» команды панели при наведении курсора мыши   

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (глиф) | `Environment.CommandBarOptionsMouseDownGlyph` |

**«Дополнительно» и «Переполнение» кнопок на панели команд: нажата состояния**  

![При нажатии кнопки «Дополнительные параметры» на панели команд](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />При нажатии кнопки «Дополнительные параметры» на панели команд  

![Активное переполнение](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Активная кнопка «Переполнение» командной строки  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (глиф) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Окна документов  
Нет необходимости реплицировать окон документов, так как они предоставляются средой Visual Studio. Однако может потребоваться использовать цвета, применяемые в окнах документов, чтобы ваш пользовательский интерфейс был согласован с этой частью среды Visual Studio.  

При использовании токенов цветов окна документов, будьте внимательны использовать их только для аналогичных элементов и всегда в парах. Если этого не сделать, который, возможно получение непредвиденных результатов в пользовательском Интерфейсе.  

### <a name="document-window-frames"></a>Рамки окна документа  
Окна документов могут быть закрепленными в интегрированной среде разработки или перемещаемыми как отдельные окна. Если окно документа является перемещаемым за пределами интегрированной среды разработки, он по-прежнему находится в контейнере документа и имеет фона, границы, текста и вкладку цветов, то же, что когда он входит в состав интегрированной среды разработки. Однако документ размещается внутри рамки, которая имеет собственные цвета фона, границы и текста. Если в контейнере документа закреплены окна инструментов, они наследуют поведение и цвет вкладок от имен токенов окна документа.  

![Закрепленное окно документа (красная линия)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Закрепленное окно документа (красная линия)  

![Плавающее окно (красная линия)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Плавающее окно (красная линия)  

| Используйте: | Не используйте: |
| --- | --- |
| ... в любом вы создаете пользовательский Интерфейс, который необходимо найти в окне документа. | ... для пользовательского интерфейса, вы не хотите автоматически изменить, если оболочка имеет темы. |

**Окно документа закрепленными или плавающими: состояние по умолчанию**  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Зависит от типа документа |
| Передний план (текст) | Зависит от типа документа |
| Border | `Environment.ToolWindowBorder` |

**Конкретное плавающей рамка окна документа: состояние по умолчанию**

![С плавающей запятой рамка окна документа с фокусом ввода, по умолчанию](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />С плавающей запятой рамка окна документа с фокусом ввода, по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ToolWindowFloatingFrame` |
| Передний план (текст) | `Environment.ToolWindowFloatingFrame` |
| Передний план (глиф) | `Environment.RaftedWindowButtonActiveGlyph` |
| Border | `Environment.MainWindowActiveDefaultBorder` |
| Граница (глиф) | `Environment.RaftedWindowButtonActiveBorder`<br />(Задается как прозрачная) |

**Рамка окна документа без фокуса ввода, с плавающей запятой: состояние по умолчанию**  

![По умолчанию рамка окна документа без фокуса ввода, с плавающей запятой](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />По умолчанию рамка окна документа без фокуса ввода, с плавающей запятой

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ToolWindowFloatingFrameInactive` |
| Передний план (текст) | `Environment.ToolWindowFloatingFrameInactive` |
| Передний план (глиф) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Border | `Environment.MainWindowInactiveBorder` |
| Граница (глиф) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Задается как прозрачная) |

**Конкретное плавающей рамка окна документа: наведите указатель мыши состояния**

![Конкретное плавающей рамка окна документа при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Конкретное плавающей рамка окна документа при наведении курсора мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон (глиф) | `Environment.RaftedWindowButtonHoverActive` |
| Передний план (глиф) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Граница (глиф) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Рамка окна документа без фокуса ввода, с плавающей запятой: наведите указатель мыши состояния**  

![Без фокуса ввода, с плавающей запятой рамка окна документа при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Без фокуса ввода, с плавающей запятой рамка окна документа при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон (глиф) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Передний план (глиф) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Граница (глиф) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Конкретное плавающей рамка окна документа: нажата состояния**  

![Конкретное плавающей рамка окна документа на машине](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Конкретное плавающей рамка окна документа на машине

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон (глиф) | `Environment.RaftedWindowButtonDown` |
| Передний план (глиф) | `Environment.RaftedWindowButtonDownGlyph` |
| Граница (глиф) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Вкладки документов  
Вкладки документов размещаются в канале вкладок и указывают, какие документы в настоящее время открыты, а также какой документ в настоящий момент выбран или активен. Окна инструментов также могут закрепляться в канале вкладок документов, если пользователь размещает их там. В этом случае для них используются те же цвета, что и для окон документов. Если вы создаете пользовательский интерфейс, цвета которого должны всегда соответствовать цветам окна документа (в том числе при обновлении темы или установке новых тем), то используйте ссылки на указанные ниже токены цветов.  

![Вкладки документов (красная линия)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Вкладки документов (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... в любом выполняется создание пользовательского интерфейса должен соответствовать вкладкам документов и автоматически изменяться при обновлении тем или добавлении новых цветов темы. | ... для пользовательского интерфейса, который должен обновляться автоматически, если оболочка имеет темы. |

#### <a name="open-document-tabs"></a>Вкладки открытых документов  
Каждый открытый документ имеет вкладку в канале вкладок документов, на которой показано его имя. Документы могут быть либо выбраны, либо открыты в фоновом режиме. На их вкладках указываются перечисленные ниже состояния.  

-   Выбранная вкладка представляет документ, который в настоящее время отображается в контейнере документа. Выбранная вкладка имеет границу документа, которая располагается по верхнему краю контейнера документа.  

-   Фоновые вкладки — это все вкладки документов, кроме выбранной в настоящий момент вкладки. При щелчке по такой вкладке она становится выбранной и получает цвета фона, границы и текста с соответствующими именами токенов.  

![Открытой вкладки документов (красная линия)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Открытой вкладки документов (красная линия)

| Используйте:  | Не используйте: |
| --- | --- |
| ... при создании пользовательских вкладок документов. | ... для вкладок временных (Предварительная версия). |
| | ... для пользовательского интерфейса, который должен обновляться автоматически, если оболочка имеет темы. |

**Вкладка выбранного документа с фокусом ввода**  

![Вкладка выбранного документа с фокусом ввода](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Вкладка выбранного документа с фокусом ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.FileTabSelectedGradientTop`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.FileTabSelectedText` |
| Border | `Environment.FileTabSelectedBorder`<br />(Значение совпадает с цветом фона). |
| Граница документа | `Environment.FileTabDocumentBorderBackground` |

**Вкладки документов выбрано, без фокуса ввода**

![Вкладки документов выбрано, без фокуса ввода](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Вкладки документов выбрано, без фокуса ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.FileTabInactiveGradientTop`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.FileTabInactiveText` |
| Border | `Environment.FileTabInactiveBorder`<br />(Значение совпадает с цветом фона). |
| Граница документа | `Environment.FileTabInactiveDocumentBorderBackground` |

**Вкладка фона документа: состояние по умолчанию**  

![Вкладка документа фона по умолчанию](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Вкладка документа фона по умолчанию  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.FileTabBackground` |
| Передний план (текст) | `Environment.FileTabText` |
| Border | `Environment.FileTabBorder`<br />(Значение совпадает с цветом фона). |

**Вкладка фона документа: наведите указатель мыши состояния**  

![Вкладка фона документа при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Вкладка фона документа при наведении курсора мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.FileTabHotGradientTop`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.FileTabHotText` |
| Border | `Environment.FileTabHotBorder`<br />(Значение совпадает с цветом фона). |

#### <a name="preview-tab"></a>Вкладка предварительного просмотра  
Также называется «временной» вкладки. Вкладка предварительного просмотра отображается в правой части канала вкладок документов, когда пользователь щелкает элемент в окне инструментов обозревателя решений. Она служит для предварительного просмотра документа и дает пользователю возможность сохранять документ открытым в левой части канала вкладок документов. Одновременно может быть открыта только одна вкладка предварительного просмотра. Так же как открытые вкладки, вкладки предварительного просмотра имеют как фоновое, так и выбранное состояния и в активном состоянии могут получать фокус ввода и терять его.  

![Вкладка предварительного просмотра (красная линия)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Вкладка предварительного просмотра (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... в любом месте, которую вы создаете Предварительный просмотр и требуется какой-либо элемент в соответствии с текущей цвета вкладки предварительного просмотра. | ... для любого типа документа или вкладки, которая не является временной (Предварительная версия). |
| | ... для пользовательского интерфейса, который должен обновляться автоматически, если оболочка имеет темы. |

**Вкладка предварительного просмотра, имеющего фокус, выбранного**  

![Вкладка предварительного просмотра, имеющего фокус, выбранного](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Вкладка предварительного просмотра, имеющего фокус, выбранного

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.FileTabProvisionalSelectedActive` |
| Передний план (текст) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Border | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Значение совпадает с цветом фона). |
| Граница документа | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Вкладка предварительного просмотра без фокуса ввода, выбранной**  

![Вкладка предварительного просмотра без фокуса ввода, выбранной](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Вкладка предварительного просмотра без фокуса ввода, выбранного

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.FileTabProvisionalSelectedInactive` |
| Передний план (текст) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Border | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Граница документа | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Фоновая вкладка предварительного просмотра: состояние по умолчанию**  

![По умолчанию фоновая вкладка предварительного просмотра](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />По умолчанию фоновая вкладка предварительного просмотра  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.FileTabProvisionalInactive` |
| Передний план (текст) | `Environment.FileTabProvisionalInactiveForeground` |
| Border | `Environment.FileTabProvisionalInactiveBorder`<br />(Значение совпадает с цветом фона). |

**Фоновая вкладка предварительного просмотра: наведите указатель мыши состояния**  

![Фоновая вкладка предварительного просмотра при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Фоновая вкладка предварительного просмотра при наведении курсора мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.FileTabProvisionalHover` |
| Передний план (текст) | `Environment.FileTabProvisionalHoverForeground` |
| Border | `Environment.FileTabProvisionalHoverBorder`<br />(Значение совпадает с цветом фона). |

#### <a name="document-overflow-button"></a>Кнопка переполнения документа  
Кнопка переполнения документа присутствует, если открыт один или несколько документов, вне зависимости от того, имеется ли в текущей конфигурации пространство по вертикали для размещения всех вкладок документов. Раскрывающемся меню переполнения документа, которая управляется [панели меню команд](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) цветов, отображает список всех открытых документов, видимыми и скрытых и глиф переполнения меняется в зависимости от того, отображаются ли все открытые документы в канале вкладок.  

![Кнопка переполнения документа (красная линия)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Кнопка переполнения документа (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... при создании пользовательской кнопки переполнения документа. | ... для пользовательского интерфейса, которые не аналогично кнопки переполнения. |
| | ... для кнопок переполнения панели команд. |

**Кнопка переполнения документа: состояние по умолчанию**  

![Кнопка переполнения документа по умолчанию](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Кнопка переполнения документа по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.DocWellOverflowButtonBackground` |
| Передний план (глиф) | `Environment.DocWellOverflowButtonGlyph` |
| Border | Н/Д |

**Кнопка переполнения документа: наведите указатель мыши состояния**

![Кнопка переполнения документа при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Кнопка переполнения документа при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Передний план (глиф) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Border | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Кнопка переполнения документа: нажата состояния**  

![Кнопка переполнения документа на машине](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Кнопка переполнения документа на машине

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Передний план (глиф) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Border | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Добавление тегов  
Visual Studio поддерживает добавление тегов, что позволяет пользователю объявлять доступные для поиска ключевые слова в целях отслеживания. Например, руководители проектов и разработчики могут использовать Team Foundation Server (TFS) для добавления тегов к рабочим элементам. В приведенных ниже таблицах представлены имена цветов как для самого тега, так и для глифа (значка закрытия), который появляется при наведении указателя и в некоторых состояниях.  

![Добавление тегов в Visual Studio (красная линия)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Добавление тегов в Visual Studio (красная линия)  

| Используйте: | Не используйте: |
| --- | --- |
| ... для пользовательского интерфейса, который поддерживает добавление тегов. | ... для любой другой тип пользовательского интерфейса. |

#### <a name="tags"></a>Теги  

**Тег: состояние по умолчанию**

![Тег по умолчанию](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Тег по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |  
| Фон | `Tag.Background` |
| Передний план (текст) | `Tag.Background` |

**Тегом: состояния наведения**  

![Тег при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Тег при наведении указателя мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |  
| Фон | `Tag.HoverBackground` |
| Передний план (текст) | `Tag.HoverBackgroundText` |

**Тег: состояние нажатия**

![Активен тег](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Активен тег  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Tag.PressedBackground` |
| Передний план (текст) | `Tag.PressedBackgroundText` |

**Тег: при выбранном состоянии**

![Выбранный тег](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Выбранный тег  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Tag.SelectedBackground` |
| Передний план (текст) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Закрыть (&times;) глиф тега

**Закрыть (&times;) глиф тега: состояние по умолчанию**

![По умолчанию Закрыть (&times;) глиф тега](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />По умолчанию Закрыть (&times;) глиф тега

| Элемент | Имя токена: Category.color |
| --- | --- |  
| Фон | Н/Д |
| Передний план (глиф) | `Tag.TagHoverGlyph` |

**Закрыть (&times;) глиф тега: наведите указатель мыши состояния**

![Закрыть (&times;) тега глиф при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Закрыть (&times;) тега глиф при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Tag.TagHoverGlyphHoverBackground` |
| Передний план (глиф) | `Tag.TagHoverGlyphHover` |
| Border | `Tag.TagHoverGlyphHoverBorder` |

**Закрыть (&times;) глиф тега: нажата состояния**

![Закрыть активный (&times;) глиф тега](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Закрыть активный (&times;) глиф тега

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Tag.TagHoverGlyphPressedBackground` |
| Передний план (глиф) | `Tag.TagHoverGlyphPressed` |
| Border | `Tag.TagHoverGlyphPressedBorder` |

**Выбран тег с закрыть (&times;) глиф: состояние по умолчанию**

![По умолчанию для выбранного тега с закрыть (&times;) глифа](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />По умолчанию для выбранного тега с закрыть (&times;) глифа

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Н/Д |
| Передний план (глиф) | `Tag.TagSelectedGlyph` |

**Выбран тег с закрыть (&times;) глиф: наведите указатель мыши состояния**  

![Выбран тег с закрыть (&times;) глиф при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Выбран тег с закрыть (&times;) глиф при наведении курсора мыши  


| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Tag.TagSelectedGlyphHoverBackground` |
| Передний план (глиф) | `Tag.TagSelectedGlyphHover` |
| Border | `Tag.TagSelectedGlyphHoverBorder` |

**Выбран тег с закрыть (&times;) глиф: нажата состояния**  

![Активный тег с закрыть, выбран (&times;) глифа](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Активный тег с закрыть, выбран (&times;) глифа

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Tag.TagSelectedGlyphPressedBackground` |
| Передний план (глиф) | `Tag.TagSelectedGlyphPressed` |
| Border | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Окна инструментов  
Нет необходимости реплицировать окна инструментов, так как они предоставляются средой Visual Studio. Однако может потребоваться использовать цвета, применяемые в окнах инструментов, чтобы ваш пользовательский интерфейс был согласован с этой частью среды Visual Studio.  

![Окно инструментов (красная линия)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Окно инструментов (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... в любом вы создаете пользовательский Интерфейс, который нужно найти совпадения окна инструментов. | ... для пользовательского интерфейса, который должен обновляться автоматически, если оболочка имеет темы. |

### <a name="tool-window-frame"></a>Рамка окна инструментов  
Окна инструментов в Visual Studio используются для множества различных задач и могут иметь одно из нескольких состояний. Если окно инструментов открыто, оно может быть назначено одной из четырех сторон области документа. Окна инструментов также могут перемещаться за пределы интегрированной среды документов, что позволяет размещать их в любом месте экрана. Перемещаемые окна всегда находятся поверх интегрированной среды разработки. Наконец, окна инструментов могут закрепляться как окна документов и отображаться в виде вкладок в контейнере документа. К окнам инструментов, закрепленным как окна документов, частично применяются имена токенов окна документа.  

![Фрейм окна инструментов (красная линия)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Фрейм окна инструментов (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... в любом вы создаете пользовательский Интерфейс, который нужно найти совпадения окна инструментов. | ... для пользовательского интерфейса, который должен обновляться автоматически, если оболочка имеет темы. |

**Закрепленное окно**  

![Закрепленное окно](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Закрепленное окно  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ToolWindowBackground` |
| Border | `Environment.ToolWindowBorder` |

**Плавающее окно, окно инструментов с фокусом ввода**

![Плавающее окно, окно инструментов с фокусом ввода](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Плавающее окно, окно инструментов с фокусом ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ToolWindowBackground` |
| Border | `Environment.MainWindowActiveDefaultBorder` |

**Плавающее окно, окно инструментов без фокуса ввода**  

![Плавающее окно, окно инструментов без фокуса ввода](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Плавающее окно, окно инструментов без фокуса ввода  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ToolWindowBackground` |
| Border | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Панели инструментов в стиле windows
Область элементов является одним из наиболее часто используемых стандартных окон инструментов в Visual Studio. Это по сути дерево с к нему специальной темой и стилем применения.  

![Окно панели элементов по принципу (красная линия)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Окно панели элементов по принципу (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... при создании окна инструментов, которое вы хотите всегда должно быть согласовано с панелью элементов оболочки. | ... для параметров, которые не похожи на панель элементов пользовательского интерфейса или если вы не уверены, ли пользовательского интерфейса могут возникнуть проблемы при изменении цветов панели элементов оболочки. |

**Узлы элементов: состояние по умолчанию**

![Родительский узел панели инструментов по умолчанию](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Родительский узел панели инструментов по умолчанию

![Дочерний узел панели инструментов по умолчанию](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Дочерний узел панели инструментов по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ToolboxContent`<br />(Заголовки) |
| Фон | `Environment.ToolWindowBackground`<br />(Отдельные элементы или все окно, если нет доступных элементов управления) |
| Border | Нет |
| Передний план (глиф) | `Environment.ToolboxContent` |
| Передний план (текст) | `Environment.ToolboxContent` |

**Дочерние узлы элементов: наведите указатель мыши состояния**

![Дочерний узел панели инструментов при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Дочерний узел панели инструментов при наведении указателя мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ToolboxContentMouseOver`<br />(Только для отдельных элементов) |
| Border | Нет |
| Передний план (текст) | `Environment.ToolboxContentMouseOver`<br />(Только для отдельных элементов) |

**Выбранные узлы элементов: состояние с фокусом ввода**

![Родительский узел панели инструментов, имеющего фокус, выбранного](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Родительский узел панели инструментов, имеющего фокус, выбранного  

![Дочерний узел панели инструментов, имеющего фокус, выбранного](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Дочерний узел панели инструментов, имеющего фокус, выбранного

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `TreeView.SelectedItemActive`<br />Из [представление в виде дерева](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) категории |
| Border | `TreeView.FocusVisualBorder`<br />Из [представление в виде дерева](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) категории |
| Передний план (глиф) | `TreeView.SelectedItemActive`<br />Из [представление в виде дерева](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) категории |
| Передний план (текст) | `TreeView.SelectedItemActive`<br />Из [представление в виде дерева](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) категории |

**Выбранные узлы элементов: состояния без фокуса ввода**

![Родительский узел панели инструментов выбранной, без фокуса ввода](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Родительский узел панели инструментов выбранной, без фокуса ввода  

![Дочерний узел панели инструментов выбранной, без фокуса ввода](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Дочерний узел панели инструментов выбранной, без фокуса ввода  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `TreeView.SelectedItemInactive`<br />Из [представление в виде дерева](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) категории |
| Border | Нет |
| Передний план (глиф) | `TreeView.SelectedItemInactive`<br />Из [представление в виде дерева](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) категории |
| Передний план (текст) | `TreeView.SelectedItemInactive`<br />Из [представление в виде дерева](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) категории |

### <a name="tool-window-title-bar"></a>Заголовок окна инструментов  
Граница заголовка окна не границей, это толстой линией в верхней части заголовка окна. Он не имеет имени токена для состояния без фокуса ввода.  

![Заголовок окна инструментов (красная линия)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Заголовок окна инструментов (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... в любом вы создаете пользовательский Интерфейс, который нужно найти совпадения окна инструментов. | ... для пользовательского интерфейса, который должен обновляться автоматически, если оболочка имеет темы. |

**Строку заголовка с фокусом ввода**

![Строку заголовка с фокусом ввода](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Заголовок окна с фокусом ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.TitleBarActiveGradientBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.TitleBarActiveText` |
| Border | `Environment.TitleBarActiveBorder`<br />(Значение совпадает с цветом фона). |
| Маркер перетаскивания | `Environment.TitleBarDragHandleActive` |

**Панель заголовка без фокуса ввода**  

![Панель заголовка без фокуса ввода](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Заголовок окна без фокуса ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.TitleBarInactiveGradientBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.TitleBarInactiveText` |
| Border | Н/Д |
| Маркер перетаскивания | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Кнопки в строке заголовка окна инструментов  
![Строка кнопки заголовка (красная линия)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Строка кнопки заголовка (красная линия)  

| Используйте: | Не используйте: |
| --- | --- |
| ... для кнопок, отображаемых в пользовательском Интерфейсе, который использует токены цветов с заголовками окон инструментов. | ... для кнопок, отображаемых в других местах. |
| | в сочетании любой фона и цвета переднего плана, отличном от определенных. |

**Кнопки в заголовке окна с фокусом ввода: состояние по умолчанию**

![По умолчанию, кнопки в строке заголовка с фокусом ввода](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />По умолчанию, кнопки в строке заголовка с фокусом ввода  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Н/Д |
| Передний план (глиф) | `Environment.ToolWindowButtonActiveGlyph` |
| Border | Н/Д |

**Кнопки панели заголовка без фокуса ввода: состояние по умолчанию**

![По умолчанию, кнопки в строке заголовка без фокуса ввода](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />По умолчанию, кнопки в строке заголовка без фокуса ввода    

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | Н/Д |
| Передний план (глиф) | `Environment.ToolWindowButtonInactiveGlyph` |
| Border | Н/Д |

**Кнопки в заголовке окна с фокусом ввода: наведите указатель мыши состояния**  

![Кнопки в строке заголовка с фокусом ввода при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Кнопки в строке заголовка с фокусом ввода при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ToolWindowButtonHoverActive` |
| Передний план (глиф) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Border | `Environment.ToolWindowButtonHoverActiveBorder` |

**Кнопки панели заголовка без фокуса ввода: наведите указатель мыши состояния**  

![Кнопки панели заголовка без фокуса ввода при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Кнопки панели заголовка без фокуса ввода при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ToolWindowButtonHoverInactive` |
| Передний план (глиф) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Border | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Кнопки в заголовке окна с фокусом ввода: нажата состояния**

![Кнопки панели заголовка с фокусом ввода на машине](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Кнопки панели заголовка с фокусом ввода на машине

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ToolWindowButtonDown` |
| Передний план (глиф) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Border | `Environment.ToolWindowButtonDownBorder` |

**Кнопки панели заголовка без фокуса ввода: нажата состояния**

![Кнопки панели заголовка без фокуса ввода на машине](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Кнопки панели заголовка без фокуса ввода на машине  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ToolWindowButtonDown` |
| Передний план (глиф) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Border | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Вкладки окна инструментов  
![Вкладка окна инструментов (красная линия)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Вкладка окна инструментов (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... в любом вы создаете пользовательский Интерфейс, который нужно найти совпадения окна инструментов. | ... для пользовательского интерфейса, который должен обновляться автоматически, если оболочка имеет темы. |

**Вкладка окна выбранных инструментов с фокусом ввода**

![Вкладка окна выбранных инструментов с фокусом ввода](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Выбранная вкладка окна инструментов с фокусом ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ToolWindowTabSelectedTab` |
| Передний план (текст) | `Environment.ToolWindowTabSelectedActiveText` |
| Border | `Environment.ToolWindowTabSelectedBorder`<br />(Значение совпадает с цветом фона). |

**Вкладка окна инструментов установлен, без фокуса ввода**  

![Вкладка окна инструментов установлен, без фокуса ввода](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Выбранная вкладка окна инструментов без фокуса ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ToolWindowTabSelectedTab` |
| Передний план (текст) | `Environment.ToolWindowTabSelectedText` |
| Border | `Environment.ToolWindowTabSelectedBorder`<br />(Значение совпадает с цветом фона). |

**Фоновая вкладка окна инструментов: состояние по умолчанию**

![По умолчанию фоновая вкладка окна инструментов](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />По умолчанию фоновая вкладка окна инструментов  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Градиента устанавливаются в одно и то же значение цвета в Visual Studio 2013.) |
| Передний план (текст) | `Environment.ToolWindowTabText` |
| Border | `Environment.ToolWindowTabBorder` |

**Фоновая вкладка окна инструментов: наведите указатель мыши состояния**

![Фоновая вкладка окна инструментов при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Фоновая вкладка окна инструментов при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Градиента устанавливаются в одно и то же значение цвета в Visual Studio 2013.) |
| Передний план (текст) | `Environment.ToolWindowTabMouseOverText` |
| Border | `Environment.ToolWindowTabMouseOverBorder`<br />(Значение совпадает с цветом фона). |  

### <a name="auto-hide-tabs"></a>Автоматически скрываемые вкладки  

![Автоматически скрываемые вкладки (красная линия)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303 107_AutoHideRedline")автоматического скрытия вкладок (красная линия)

| Используйте: | Не используйте: |
| --- | --- |
| ... в любом вы создаете пользовательский Интерфейс, который нужно найти совпадения вкладки окна инструментов автоматически скрыто. | ... для пользовательского интерфейса, который должен обновляться автоматически, если оболочка имеет темы. |

**Автоматически скрываемые вкладки: состояние по умолчанию**  

![Вкладка автоматического скрытия по умолчанию](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Автоматически скрываемая вкладка по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.AutoHideTabBackgroundBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.AutoHideTabText` |
| Border | `Environment.AutoHideTabBorder` |

**Автоматически скрываемые вкладки: наведите указатель мыши состояния**

![Вкладка автоматического скрытия при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Вкладка автоматического скрытия при наведении курсора мыши  

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Градиента для данного маркера, не используется в теме пользовательского интерфейса.) |
| Передний план (текст) | `Environment.AutoHideTabMouseOverText` |
| Border | `Environment.AutoHideTabMouseOverBorder` |

