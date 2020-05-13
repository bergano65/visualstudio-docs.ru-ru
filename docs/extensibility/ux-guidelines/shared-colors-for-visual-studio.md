---
title: Общие цвета для визуальной студии Документы Майкрософт
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e31e5d9c3d1dc284694bd2db2a9f37d863462ad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699931"
---
# <a name="shared-colors-for-visual-studio"></a>Общие цвета для визуальной студии
При проектировании интерфейса, используюго общие элементы оболочки Visual Studio, или вы хотите, чтобы элемент интерфейса соответствовал аналогичным функциям, используйте существующие имена маркеров в файлах определения пакетов для выбора и назначения цветов. Таким образом можно обеспечить согласованность пользовательского интерфейса со всей средой Visual Studio и его автоматическое обновление при добавлении или обновлении тем.

В этом разделе описываются стандартные элементы пользовательского интерфейса и используемые ими имена токенов, на которые можно ссылаться при разработке похожего пользовательского интерфейса. Более подробные сведения о доступе к этим токенам цветов см. в разделе [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Используйте имена токенов правильно.

- **Используйте имена токенов в соответствии с функцией, а не самим цветом.** Стандартные общие цвета связаны с определенными элементами интерфейса и предназначены для использования только для аналогичных или похожих функций. Например, не используйте цвет выбранного поля со списком для анимированного индикатора хода выполнения только потому, что вам понравился цвет. Функции комбо-коробки и анимации различны, и если цвет, связанный с комбо-коробкой, изменяется, он может больше не быть подходящим цветом для элемента анимации. Согласованное использование цветов помогает пользователям ориентироваться в интерфейсе и предотвращает путаницу.

- **Используйте цвета фона и текста в правильном сочетании.** Цвет фона, предназначенный для текста, имеет соответствующий цвет текста. Не используйте цвета текста, отличные от тех, которые определены для данного цвета фона. Если нет связанного цвета текста, не используйте этот цвет фона для любой поверхности, на которой вы ожидаете отображения текста. Другие комбинации цветов текста и фона могут привести к нечитаемому интерфейсу.

- **Используйте цвета элементов управления, соответствующие их расположению.** В некоторых штатах некоторые элементы управления Visual Studio не имеют отдельных пограничных и фоновых цветов. Эти цвета наследуются от областей, в которых они расположены. Всегда используйте имена токенов, которые подходят для того места, в котором вы размещаете элементы управления.

> [!IMPORTANT]
> Не используйте токены, найденные в категориях "Старт-страница" или "Сидр".

## <a name="common-shared-controls"></a>Стандартные общие элементы управления

При использовании стандартной панели команд Visual Studio в вашей функции, вы будете иметь доступ к стилизованным элементам управления оболочкой. Вы не должны повторно шаблон этих общих элементов управления. Однако если вам нужно создать пользовательскую панель команд, вам также может потребоваться создать пользовательские элементы управления. В этом случае используйте правильные имена токенов для каждого из указанных ниже элементов управления, чтобы ваш пользовательский интерфейс был согласован с остальной средой Visual Studio.

### <a name="button-controls"></a>Элементы управления "Кнопка"

![Красная линия элемента управления "Кнопка"](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Использовать... | Не используйте ... |
| --- | --- |
| ... для кнопок в документе хорошо, что вы хотите интегрировать с Visual Studio темы (Свет, Темный, Синий, или тема высокой контрастной системы). | ... для кнопок, которые будут отображаться на пользовательском фоне, который не является частью темы Visual Studio. |

**Кнопка: стандартное состояние**

![Стандартная кнопка](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Стандартная кнопка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.Button` |
| Граница кнопки | `CommonControls.ButtonBorder` |

**Кнопка: состояние по умолчанию**

![Кнопка по умолчанию](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Кнопка по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.ButtonDefault` |
| Граница кнопки | `CommonControls.ButtonBorderDefault` |

**Кнопка: отключенное состояние**

![Кнопка отключения](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Кнопка.Инвалид")<br />Кнопка отключения

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.ButtonDisabled` |
| Граница кнопки | `CommonControls.ButtonBorderDisabled` |

**Кнопка: состояние нависки**

![Кнопка при наведении курсора мыши](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Кнопка при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.ButtonHover` |
| Граница кнопки | `CommonControls.ButtonBorderHover` |

**Кнопка: нажатое состояние**

![Нажатие кнопки](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Нажатие")<br />Нажатие кнопки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.ButtonPressed` |
| Граница кнопки | `CommonControls.ButtonBorderPressed` |

**Кнопка: сфокусированное состояние**

![Кнопка фокусировки](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused.Focused")<br />Кнопка фокусировки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Кнопка | `CommonControls.ButtonFocused` |
| Граница кнопки | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Элементы управления "Флажок"
![Флажок (красная линия)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Флажок (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... для управления флажок, содержащихся в документе хорошо. | ... для любого uI, который не является контролем флажка. |

**Проверить окно: состояние по умолчанию**

![Флажок](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Флажок по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.CheckBoxBackground` |
| Border | `CommonControls.CheckBoxBorder` |
| Text | `CommonControls.CheckBoxText` |
| Глиф | `CommonControls.CheckBoxGlyph` |

**Проверить окно: отключенное состояние**

![Инвалид флажок](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Инвалид флажок

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.CheckBoxBackgroundDisabled` |
| Border | `CommonControls.CheckBoxBorderDisabled` |
| Text | `CommonControls.CheckBoxTextDisabled` |
| Глиф | `CommonControls.CheckBoxGlyphDisabled` |

**Проверить окно: состояние нависать**

 ![Флажок при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Флажок при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.CheckBoxBackgroundHover` |
| Border | `CommonControls.CheckBoxBorderHover` |
| Text | `CommonControls.CheckBoxTextHover` |
| Глиф | `CommonControls.CheckBoxGlyphHover` |

**Проверить окно: нажатое состояние**

![Прессованный флажок](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Прессованный флажок

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.CheckBoxBackgroundPressed` |
| Border | `CommonControls.CheckBoxBorderPressed` |
| Text | `CommonControls.CheckBoxTextPressed` |
| Глиф | `CommonControls.CheckBoxGlyphPressed` |

**Проверить окно: сфокусированное состояние**

![Фокусированный флажок](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Фокусированный флажок

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.CheckBoxBackgroundFocused` |
| Border | `CommonControls.CheckBoxBorderFocused` |
| Text | `CommonControls.CheckBoxTextFocused` |
| Глиф | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Выпадающие и комбо-коробки
![Выпадающий/комбо-бокс (красная линия)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Выпадающий/комбо-бокс (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... для выпадения и комбо коробки в документе хорошо. | ... для любого uI, который не является выпадающим или комбо-бокс. |
| | ... для команды бар [падения](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) или [комбо коробки](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Выпадение и комбо-коробки: состояние по умолчанию**

![По умолчанию выпадение вниз / комбо окно](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />По умолчанию выпадение вниз / комбо окно

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.ComboBoxBackground` |
| Border | `CommonControls.ComboBoxBorder` |
| Text | `CommonControls.ComboBoxText` |
| Separator | `CommonControls.ComboBoxSeparator` |
| Глиф | `CommonControls.ComboBoxGlyph` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackground` |

**Выпадение и комбо-коробки: состояние инвалидов**

![Инвалид выпадение вниз / комбо окно](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Инвалид выпадение вниз / комбо окно

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.ComboBoxBackgroundDisabled` |
| Border | `CommonControls.ComboBoxBorderDisabled` |
| Text | `CommonControls.ComboBoxTextDisabled` |
| Separator | `CommonControls.ComboBoxSeparatorDisabled` |
| Глиф | `CommonControls.ComboBoxGlyphDisabled` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Падение и комбо-коробки: состояние нависания**

![Раскрывающийся список/поле со списком при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Раскрывающийся список/поле со списком при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.ComboBoxBackgroundHover` |
| Border | `CommonControls.ComboBoxBorderHover` |
| Text | `CommonControls.ComboBoxTextHover` |
| Separator | `CommonControls.ComboBoxSeparatorHover` |
| Глиф | `CommonControls.ComboBoxGlyphHover` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Выпадение и комбо-коробки: нажатое состояние**

![Прессованные выпадающие/комбо-бокс](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Прессованные выпадающие/комбо-бокс

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.ComboBoxBackgroundPressed` |
| Border | `CommonControls.ComboBoxBorderPressed` |
| Text | `CommonControls.ComboBoxTextPressed` |
| Separator | `CommonControls.ComboBoxSeparatorPressed` |
| Глиф | `CommonControls.ComboBoxGlyphPressed` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Выпадение и комбо-боксы список элементов зрения: нажата состояние**

 ![Выпадение вниз / комбо окно нажата список элементов представления](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Выпадение вниз / комбо окно нажата список элементов представления

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Border | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Текст элемента | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Фон с тенью | `CommonControls.ComboBoxListBackgroundShadow` |

**Выпадение и комбо-коробки: сфокусированное состояние**

![Выпадающий/комбо-бокс с фокусом](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Выпадающий/комбо-бокс с фокусом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.ComboBoxBackgroundFocused` |
| Border | `CommonControls.ComboBoxBorderFocused` |
| Text | `CommonControls.ComboBoxTextFocused` |
| Separator | `CommonControls.ComboBoxSeparatorFocused` |
| Глиф | `CommonControls.ComboBoxGlyphFocused` |
| Фон глифа | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Выпадающие и комбо-коробки: выбор ввода текста**

![Выпадение/комбо-коробка выбор текста ввода](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Выпадение/комбо-коробка выбор текста ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Выделение | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Табличные элементы управления данными (сетка)
Табличные элементы управления данными, также называемые элементами управления "Сетка", — это стандартные элементы управления Visual Studio, которые можно использовать для представления больших объемов данных в нескольких столбцах. Стандартные табличные элементы управления данными встречаются в Visual Studio в нескольких местах: в окне инструментов "Список ошибок", в отчетах IntelliTrace, в представлении кучи памяти и т. д. Всегда используйте стандартные табличные элементы управления данными. Однако в некоторых редких случаях доступ к стандартным табличным элементам управления данными может отсутствовать. В таких ситуациях используйте указанные ниже имена токенов для обеспечения согласованности пользовательского интерфейса с другими табличными элементами управления данными в Visual Studio.

![Табулярный контроль данных/сетки (красная линия)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Табулярный контроль данных/сетки (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... для табликов или элементов управления. | ... для любого uI, который не является табликным или сетевым управлением. |

#### <a name="column-headers"></a>Заголовки столбцов
Заголовки столбцов состоят из фона, границы, текста заголовка и необязательного глифа, который обычно используется при сортировке сетки по данному столбцу.

**Заголовок столба: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Header.Default` |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Header.Glyph` |
| Border | `Header.SeparatorLine` |

**Заголовок столба: состояние нависки**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Header.MouseOver` |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Передний план (глиф) | `Header.MouseOverGlyph` |
| Border | `Header.SeparatorLine` |

**Заголовок столбца: нажатое состояние**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `CommonControls.CheckBoxBackgroundPressed` |
| Передний план (текст) | `CommonControls.CheckBoxBorderPressed` |
| Передний план (глиф) | `CommonControls.CheckBoxTextPressed` |
| Border | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Элементы представления списка
 Элементы представления списка состоят из фона и содержимого. Содержимым может быть текст, значок или и то и другое.

**Элементы представления списка: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Прозрачный |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Border | Отсутствуют |

**Элементы представления списка: активное состояние**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemActive` |
| Передний план (текст) | `TreeView.SelectedItemActiveText` |
| Border | Отсутствуют |

**Элементы представления списка: неактивное состояние**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemInactive` |
| Передний план (текст) | `TreeView.SelectedItemInactiveText` |
| Border | Отсутствуют |

### <a name="ui-text"></a>Текст uI

#### <a name="instructional-text"></a>Учебный текст
Учебный текст дает важное главное объяснение того, что делать на странице диалога или документа.

![Учебный текст по умолчанию](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Учебный текст по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Вторичный учебный текст
На страницах документов с большим количеством текста и элементов управления в некоторых учебных текстах используется другое цветовое значение. Это помогает передать, какая информация является наиболее важной, и уменьшает общую плотность элементов uI. (См. также ниже раздел на текст подсказки.)

![Вторичный учебный текст](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Вторичный учебный текст

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Подсказка текст
Подсказка текст появляется в пустой элемент управления, ниже элемента управления, или на пустой поверхности документа, чтобы показать пользователю, что делать дальше. Текст подсказки можно использовать с фоном Window или Control.

**Текст подсказки по умолчанию**

![Текст подсказки по умолчанию](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Текст подсказки по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.ControlEditHintText` |

**Обязательный текст подсказки**

![Обязательный текст подсказки](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Обязательный текст подсказки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.ControlRequiredHintText` |
| Историческая справка | `Environment.ControlRequiredBackground` |

**Текст управления окном поиска**

> Смотрите [поиск коробок](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) для других цветовых токенов, связанных с управлением поиска.

![Текст управления окном поиска](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Текст управления окном поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
Гиперссылка — это один элемент управления, который не имеет передний план/фоновую пару. Во всех случаях используйте цвет гиперссылки на переднем плане, который будет правильно отображаться на темном, сером и белом фоне. Если вы не используете цветной маркер для управления гиперссылкой, вы увидите цвет системы по умолчанию для "нажатия", который будет мигать красным цветом. Это сигнал о том, что элемент управления не использует токен цвета правильной среды.

![Гиперссылка (красная линия)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Гиперссылка (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... когда вам нужно создать пользовательскую гиперссылку. | ... за все, что не является гиперссылкой. |

**Гиперссылка: состояние по умолчанию**

![Гиперссылка по умолчанию](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Гиперссылка по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlink` |

**Гиперссылка: состояние нависки**

![Гиперссылка при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Гиперссылка при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlinkHover` |

**Гиперссылка: нажатое состояние**

![Прессованная гиперссылка](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Прессованная гиперссылка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlinkPressed` |

**Гиперссылка: состояние отключений**

![Гиперссылка для инвалидов](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Гиперссылка для инвалидов

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Инфобарс
Информационные панели служат для предоставления дополнительной информации о данном контексте и всегда отображаются в верхней части окна документа или окна инструментов.

![Инфобар (красная линия)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Инфобар (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... при создании пользовательских инфобаров. | ... для элементов uI, которые не похожи на infobar. |

**Infobar: состояние по умолчанию**

![Инфопанель по умолчанию](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Инфопанель по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.InfoBarBackground` |
| Передний план (текст) | `InfoBar.InfoBar` |
| Border | `InfoBar.InfoBarBorder` |

**Infobar Закрыть&times;( ) кнопка: состояние по умолчанию**

![По умолчанию&times;infobar Закрыть ( ) кнопка](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />По умолчанию&times;infobar Закрыть ( ) кнопка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.CloseButton` |
| Border | `InfoBar.CloseButtonBorder` |
| Глиф | `InfoBar.CloseButtonGlyph` |

**Infobar Закрыть&times;( ) кнопка: состояние нависнуть**

![Infobar Закрыть&times;( ) кнопка на навешие](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Infobar Закрыть&times;( ) кнопка на навешие

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.CloseButtonHover` |
| Border | `InfoBar.CloseButtonHoverBorder` |
| Глиф | `InfoBar.CloseButtonHoverGlyph` |

**Infobar Закрыть&times;( ) кнопка: нажато ежем состоянии**

![Нажатие Infobar&times;Закрыть ( ) кнопка](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Нажатие Infobar&times;Закрыть ( ) кнопка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.CloseButtonDown` |
| Border | `InfoBar.CloseButtonDownBorder` |
| Глиф | `InfoBar.CloseButtonDownGlyph` |

**Кнопка гиперссылки Infobar: состояние по умолчанию**

![Кнопка гиперссылки infobar по умолчанию](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Кнопка гиперссылки infobar по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `InfoBar.Hyperlink` |

**Кнопка гиперссылки Infobar: состояние навистого**

![Кнопка гиперссылки Infobar на нависнуть](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Кнопка гиперссылки Infobar на нависнуть

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseOver`<br />(С подчеркнутом) |

**Кнопка гиперссылки Infobar: нажатое состояние**

![Нажатие кнопки гиперссылки infobar](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Нажатие кнопки гиперссылки infobar

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseDown`<br />(С подчеркнутом) |

**Инфобарная вливая гиперссылка (в пределах предложения): состояние по умолчанию**

![По умолчанию влиневая кнопка гиперссылки infobar](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />По умолчанию влиневая кнопка гиперссылки infobar

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `InfoBar.Hyperlink` |

**Infobar вневательная гиперссылка (в пределах предложения): состояние навистого**

![Кнопка infobar внеконтактная гиперссылка на навешие](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Кнопка infobar внеконтактная гиперссылка на навешие

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseOver`<br />(С подчеркнутом) |

**Infobar вневинная гиперссылка (в пределах предложения): нажатое состояние**

![Нажатие кнопки инфобара виной гиперссылки](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Нажатие кнопки инфобара виной гиперссылки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Infobar.HyperlinkMouseDown`<br />(С подчеркнутом) |

**Кнопка Infobar: состояние по умолчанию**

![Кнопка инфопанели по умолчанию](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Кнопка инфопанели по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.Button` |
| Передний план (текст) | `InfoBar.Button` |
| Border | `InfoBar.ButtonBorder` |

**Кнопка Infobar: состояние навистого**

![Кнопка Infobar на нависнуть](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Кнопка Infobar на нависнуть

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.ButtonMouseOver` |
| Передний план (текст) | `InfoBar.ButtonMouseOver` |
| Border | `InfoBar.ButtonMouseOverBorder` |

**Кнопка Infobar: нажатое состояние**

![Нажатие кнопки infobar](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Нажатие кнопки infobar

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.ButtonMouseDown` |
| Передний план (текст) | `InfoBar.ButtonMouseDown` |
| Border | `InfoBar.ButtonMouseDownBorder` |

**Кнопка Infobar: отключенное состояние**

![Кнопка "Отключенная информация"](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Кнопка "Отключенная информация"

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.ButtonDisabled` |
| Передний план (текст) | `InfoBar.ButtonDisabled` |
| Border | `InfoBar.ButtonDisabledBorder` |

**Кнопка Infobar: сфокусированное состояние**

![Кнопка infobar](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Кнопка infobar

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `InfoBar.ButtonFocus` |
| Передний план (текст) | `InfoBar.ButtonFocus` |
| Border | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Полосы прокрутки
Прокрутка баров стилизованы под среду Visual Studio, и не должны быть тематическими. Тем не менее, вы можете решить, что вы хотите использовать цвета, используемые в барах прокрутки, так что ваш uI всегда отображается в соответствии с этой частью среды Visual Studio.

![Прокрутка бар (красная линия)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Прокрутка бар (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... при создании единоборсь с использованием единоборсь с использованием единоборсь с прокрутками Visual Studio. | ... для чего-либо вы не хотите, чтобы всегда соответствовать прокрутки бар uI. |

**Панель прокрутки: состояние по умолчанию**

![Панель прокрутки по умолчанию](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Панель прокрутки по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Полоса прокрутки | `Environment.ScrollBarBackground` |
| Передний план (бегунок) | `Environment.ScrollBarThumbBackground` |

**Панель прокрутки: состояние навистого**

![Полоса прокрутки при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Полоса прокрутки при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Полоса прокрутки | `Environment.ScrollBarBackground` |
| Передний план (бегунок) | `Environment.ScrollBarThumbMouseOverBackground` |

*Панель прокрутки: нажатое состояние**

![Нажатая панель прокрутки](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Нажатая панель прокрутки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Полоса прокрутки | `Environment.ScrollBarBackground` |
| Передний план (бегунок) | `Environment.ScrollBarThumbPressedBackground` |

**Стрелка панели прокрутки: состояние по умолчанию**

![Стрелка панели прокрутки по умолчанию](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Стрелка панели прокрутки по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ScrollBarArrowBackground`<br />(Установите тот же цвет, что и прокрутка бар.) |
| Передний план (глиф) | `Environment.ScrollBarArrowGlyph` |

**Стрелка панели прокрутки: состояние нависать**

![Стрелки полосы прокрутки при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Стрелки полосы прокрутки при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ScrollBarArrowMouseOverBackground`<br />(Установите тот же цвет, что и прокрутка бар.) |
| Передний план (глиф) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Стрелка панели прокрутки: нажатое состояние**

![Прессованные стрелки панели прокрутки](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Прессованные стрелки панели прокрутки

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ScrollBarArrowPressedBackground`<br />(Установите тот же цвет, что и прокрутка бар.) |
| Передний план (глиф) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Поиск коробок
По возможности используйте стандартный элемент управления поиском, предоставляемый средой Visual Studio. Цвета поля поиска находятся в категории SearchControl в файле **ShellColors.pkgdef** , который содержит имена токенов для поля ввода, управляющей кнопки, кнопки раскрывающегося списка и раскрывающегося меню.

Поле поиска может находиться в одном из нескольких состояний. Некоторые из них взаимоисключающие.

- "С фокусом ввода" или "без фокуса ввода" указывает на то, находится ли курсор в текстовом поле.

- "Активно" или "неактивно" указывает на то, ввел ли пользователь запрос в текстовом поле.

- "При наведении указателя" означает, что пользователь навел указатель мыши на поле поиска (это состояние переопределяет все остальные).

- "Отключено" означает, что функция поиска в текущем контексте отключена.

![Коробка поиска (красная линия)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Коробка поиска (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... при проектировании пользовательского окна поиска. | ... для всего, что не является полем поиска. |
| | ... для всего, что вы не хотите, чтобы всегда соответствовать uI поле поиска. |

**Целенаправленное поле ввода поиска**

![Целенаправленное поле ввода поиска](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Целенаправленное поле ввода поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.FocusedBackground` |
| Передний план (текст) | `SearchControl.FocusedBackground` |
| Border | `SearchControl.FocusedBorder` |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Нецеленаправленное, активное поле ввода поиска**

![Поле ввода окна поиска без фокуса ввода](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Нецеленаправленное, активное поле ввода поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.SearchActiveBackground` |
| Передний план (текст) | `SearchControl.SearchActiveBackground` |
| Border | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Нецеленаправленное, неактивное поле ввода поиска**

![Нецеленаправленное, неактивное поле ввода поиска](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Нецеленаправленное, неактивное поле ввода поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.Unfocused` |
| Передний план (текст) | `SearchControl.Unfocused` |
| Border | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Выделенное поле ввода поиска (только текст)**

![Выделенное поле ввода поиска](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Выделенное поле ввода поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.Selection` |
| Передний план (текст) | `SearchControl.FocusedBackground` |
| Border | Отсутствуют |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Поле ввода поиска отключено**

![Поле ввода поиска отключено](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Поле ввода поиска отключено

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.Disabled` |
| Передний план (текст) | `SearchControl.Disabled` |
| Border | `SearchControl.DisabledBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Кнопка сфокусированного действия поиска**

![Кнопка поиска с фокусом ввода](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Кнопка сфокусированного действия поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (глиф поиска) | `SearchControl.SearchGlyph` |
| Передний план (глиф остановки) | `SearchControl.StopGlyph` |
| Передний план (глиф очистки) | `SearchControl.ClearGlyph` |
| Border | Недоступно |

**Кнопка несфокусированного действия поиска**

![Кнопка несфокусированного действия поиска](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Кнопка несфокусированного действия поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Недоступно |
| Передний план (глиф поиска) | `SearchControl.SearchGlyph` |
| Передний план (глиф остановки) | `SearchControl.StopGlyph` |
| Передний план (глиф очистки) | `SearchControl.ClearGlyph` |
| Border | Недоступно |

**Нажатие кнопки действий поиска**

![Нажатие кнопки действий поиска](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Нажатие кнопки действий поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.ActionButtonMouseDown` |
| Передний план (глиф) | `SearchControl.ActionButtonMouseDownGlyph` |
| Border | `SearchControl.ActionButtonMouseDownBorder` |

**Кнопка действий по поиску отключена**

![Неактивная кнопка поиска](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Кнопка действий по поиску отключена

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (глиф) | `SearchControl.ActionButtonDisabledGlyph` |
| Border | Отсутствуют |

**Кнопка сфокусированного поиска выпадения**

![Кнопка сфокусированного поиска выпадения](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Кнопка сфокусированного поиска выпадения

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.FocusedDropDownButton` |
| Передний план (глиф) | `SearchControl.FocusedDropDownButtonGlyph` |
| Border | `SearchControl.FocusedDropDownButtonBorder` |

**Нефокусированная кнопка выпадения поиска**

![Нефокусированная кнопка выпадения поиска](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Нефокусированная кнопка выпадения поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.UnfocusedDropDownButton` |
| Передний план (глиф) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Border | `SearchControl.UnfocusedDropDownButtonBorder` |

**Нажатие кнопки выпадения поиска**

![Нажатие кнопки выпадения поиска](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Нажатие кнопки выпадения поиска

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.MouseDownDropDownButton` |
| Передний план (глиф) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Border | `SearchControl.MouseDownDropDownButtonBorder` |

**Кнопка поиска инвалидов**

![Кнопка поиска инвалидов](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Кнопка поиска инвалидов

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (глиф) | `SearchControl.DisabledDownButtonGlyph` |
| Border | Отсутствуют |

#### <a name="search-drop-down-lists"></a>Раскрывающиеся списки поиска
Меню выпадающих полей поиска может быть немного более сложным, чем другие выпадающие меню в Visual Studio. Разделы "предлагаемые поиски" и "варианты поиска" могут отображаться в одиночку или вместе в меню, и каждый из них окрашен отдельно. Если имеются оба этих раздела, они разделяются линией, а все раскрывающееся меню окружено границей.

![Список выпадающих поисковых систем (красная линия)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Список выпадающих поисковых систем (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... при создании пользовательского списка выпадающих поисковых систем. | ... для списков выпадающих, которые отображаются в других контекстах. |
| ... правильные имена маркеров для правильных компонентов списка. | ... в любом фоновом/переднем сочетании, кроме указанного. |

**Элементы списка выпадающих данных**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Border | `SearchControl.PopupBorder` |
| Separator | `SearchControl.PopupSectionHeaderSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Рекомендуемые поиски: состояние по умолчанию**

![По умолчанию предложил поиск](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />По умолчанию предложил поиск

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `SearchControl.PopupItemText` |

**Рекомендуемые поиски: состояние нависки**

![Предлагаемые поиски на нависке](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Предлагаемые поиски на нависке

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `SearchControl.PopupMouseOverItemText` |
| Border | `SearchControl.PopupControlMouseOverBorder` |

**Параметры поиска: состояние по умолчанию**

![Флажок поиска](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Параметры поиска по умолчанию (чек-бокс)

![Варианты поиска](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Параметры поиска по умолчанию (ссылка)

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст флажка) | `SearchControl.PopupCheckboxText` |
| Передний план (текст ссылки) | `SearchControl.PopupButtonText` |
| Фон заголовка | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст заголовка) | `SearchControl.PopupSectionHeaderText` |

**Параметры поиска: состояние нависки**

![Параметры поиска (чек-бокс) на нависчении](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Параметры поиска (чек-бокс) на нависчении

![Параметры поиска (ссылка) на нависшие](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Параметры поиска (ссылка) на нависшие

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст флажка) | `SearchControl.PopupCheckboxMouseDownText` |
| Передний план (текст ссылки) | `SearchControl.PopupButtonMouseDownText` |
| Border | `SearchControl.PopupControlMouseOverBorder` |

**Параметры поиска: нажатое состояние**

![Параметры поиска отжатых (флажок)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Параметры поиска отжатых (флажок)

![Параметры поиска (ссылка)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Параметры поиска (ссылка)

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон флажка | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст флажка) | `SearchControl.PopupCheckboxMouseDownText` |
| Фон ссылки | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст ссылки) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a>Виды деревьев
Несколько окон инструментов, включая Solution Explorer, Server Explorer и Class View, реализуют `TreeView` иерархическую организационную схему, цвета которой контролируются цветными именами в категории. Все элементы в иерархическом представлении имеют цвета фона и текста. Элементы с вложенными дочерними элементами также имеют глифы, которые указывают на то, является ли элемент свернутым или развернутым.

![Вид дерева (красная линия)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Вид дерева (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... в любом месте необходимо реализовать иерархическое организационное представление. | ... для всего, что не похоже на вид дерева. |
| | ... в любом фоновом/переднем сочетании, кроме указанного. |

**Элемент представления дерева: состояние по умолчанию**

![Элемент представления дерева по умолчанию](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Элемент представления дерева по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.Background` |
| Передний план (текст) | `TreeView.Background` |
| Передний план (глиф) | `TreeView.Glyph` |
| Border | Отсутствуют |

**Элемент представления дерева: состояние нависать**

![Элемент представления дерева на нависении](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Элемент представления дерева на нависении

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.Background` |
| Передний план (текст) | `TreeView.Background` |
| Передний план (глиф) | `TreeView.GlyphMouseOver` |
| Border | Отсутствуют |

**Элемент представления дерева: перетащите состояние**

![Элемент представления дерева на перетаскивании](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Элемент представления дерева на перетаскивании

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.DragOverItem` |
| Передний план (текст) | `TreeView.DragOverItem` |
| Передний план (глиф) | `TreeView.DragOverItemGlyph` |
| Border | Отсутствуют |

**Элемент представления дерева: выбранное, сфокусированное состояние**

![Выбранный и сфокусированный элемент представления дерева](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Выбранный и сфокусированный элемент представления дерева

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemActive` |
| Передний план (текст) | `TreeView.SelectedItemActive` |
| Передний план (глиф) | `TreeView.SelectedItemActiveGlyph` |
| Border | `TreeView.FocusVisualBorder` |

**Элемент представления дерева: выбранное, нефокусированное состояние**

![Выбранный и нефокусированный элемент представления дерева](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Выбранный и нефокусированный элемент представления дерева

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemInactive` |
| Передний план (текст) | `TreeView.SelectedItemInactive` |
| Передний план (глиф) | `TreeView.SelectedItemInactiveGlyph` |
| Border | Отсутствуют |

**Элемент представления дерева: завис, выбранный и сфокусированный состояние**

![Выбранный и сфокусированный элемент представления дерева на навискании](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Выбранный и сфокусированный элемент представления дерева на навискании

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemActive` |
| Передний план (текст) | `TreeView.SelectedItemActive` |
| Передний план (глиф) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Border | `TreeView.FocusVisualBorder` |

**Элемент представления дерева: завис, выбранный и нефокусированный состояние**

![Выбранный и нефокусированный элемент представления дерева на навискании](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Выбранный и нефокусированный элемент представления дерева на навискании

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemInactive` |
| Передний план (текст) | `TreeView.SelectedItemInactive` |
| Передний план (глиф) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Border | Отсутствуют |

## <a name="shell-appearance"></a>Внешний вид оболочки

### <a name="background"></a>Историческая справка
Фон среды состоит из двух слоев. Нижний слой представляет собой сплошной цвет, который охватывает всю интегрированную среду разработки. Верхний слой используется под командной полкой и между каналами автоматического скрытия окон инструментов по левому и правому краям интегрированной среды разработки. Верхние и нижние фоновые слои установлены на один и тот же цвет в светлых и темных темах.

![Фон оболочки визуальной студии (красная линия)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Фон оболочки визуальной студии (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... для мест, где вы хотите соответствовать фону среды Visual Studio. | ... как заливка для мест, которые не являются фоновыми поверхностями. |
| | ... в качестве фона для размещения элементов переднего плана. |

**Внешний вид оболочки нижнего слоя**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.EnvironmentBackground` |

**Внешний вид оболочки верхнего слоя**

> Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Командная полка
Для фона командной полки используются два набора имен токенов: один для области размещения строки меню, а другой — для области размещения панелей команд. Отдельные группы на панели команд имеют собственные значения цветов фона, которые более подробно рассматриваются в разделе, посвященном панели команд. Цвета текста строки меню и панели команд рассматриваются в разделах, посвященных меню и панели команд.

![Командная полка Visual Studio (красная линия)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Командная полка Visual Studio (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... для областей, где вы размещаете меню или панели инструментов. | ... для областей, не похожих на командную полку. |
|... с правильной комбинацией маркеров фона/переднего плана. | |

**Панель меню командной полки**

> Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Панель командного управления командой командования**

> Ограничения градиента устанавливаются в светлой и темной темах Visual Studio 2013 в одно значение цвета.

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Конструктор манифеста
Конструктор манифеста призван упростить редактирование файла манифеста в проектах Windows 8 и Windows Phone 8. Хотя общего готового шаблона нет, рекомендуется обеспечивать соответствие макету и цветам вкладок ориентации и навигации, а также общей структуре. Дополнительные сведения о макете см. в разделе [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Манифест Конструктор (красная линия)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Манифест Конструктор (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... для дизайнеров, которые похожи на Манифест Дизайнер. | ... если у вас есть более шести вкладок. |
| ... вместо использования общих элементов управления вкладками в верхней части редактора в документе хорошо. | ... для любого uI, который не структурирован как Manifest Designer. |

**Выбранная вкладка manifest Designer: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `ManifestDesigner.TabActive` |
| Border | Отсутствуют |

**Манифест Дизайнер выбрано описание панели: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `ManifestDesigner.DescriptionPane` |

**Страница содержимого Manifest Designer: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `ManifestDesigner.Background` |
| Текст подсказки для диалогового окна | `ManifestDesigner.WatermarkText`<br />(Это имя маркера не соответствует его функции.) |

**Вкладка manifest Designer: невыбранное состояние**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `ManifestDesigner.Tab.Inactive` |

**Вкладка manifest Designer: состояние навистого:**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Структура команд

### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Меню
Меню может происходить в нескольких местах в Visual Studio: главном баре меню, встроенном в окна документа или инструмента, или справа на кнопку в различных местах по всему IDE. Реализация меню, связанных с другими элементами пользовательского интерфейса, рассматривается в разделах, посвященных соответствующим элементам. Всегда используйте стандартную реализацию меню, предоставляемую средой Visual Studio. Однако в некоторых редких случаях доступ к стандартным меню Visual Studio может отсутствовать. В таких ситуациях используйте указанные ниже имена токенов для обеспечения согласованности пользовательского интерфейса с другими меню в Visual Studio.

![Меню визуальной студии (красная линия)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Меню визуальной студии (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... когда вам нужно создать пользовательское меню.| ... фоновый цвет в одиночку. Всегда используйте определенное сочетание цвета фона и цвета переднего плана. |
| ... когда у вас есть новый компонент uI, который вы хотите соответствовать меню Visual Studio.| |

#### <a name="menu-titles"></a>Названия меню
Заголовок меню состоит из фона, границы и текста заголовка, а также необязательного глифа (обычно если меню находится на панели команд).

![Название меню (красная линия)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Название меню (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... всякий раз, когда вы создаете пользовательское название меню. | ... за все, что вы не хотите, чтобы всегда соответствовать названию меню. |
| | ... в любом фоновом/переднем сочетании, кроме указанного. |

**Заголовок меню: состояние по умолчанию**

![Название меню по умолчанию](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Название меню по умолчанию

![Название меню по умолчанию с глифом](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Название меню по умолчанию с глифом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Environment.CommandBarMenuGlyph` |
| Border | Отсутствуют |

**Название меню: состояние навистого**

![Заголовок меню при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Заголовок меню при наведении курсора мыши

![Заголовок меню с глифом при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Заголовок меню с глифом при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Передний план (глиф) | `Environment.CommandBarMenuMouseOverGlyph` |
| Border | `Environment.CommandBarBorder` |

**Название меню: нажатое состояние**

![Название меню отжатое](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Название меню отжатое

![Название меню с глифом](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Название меню с глифом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Environment.CommandBarMenuMouseDownGlyph` |
| Border | `Environment.CommandBarMenuBorder`<br />(Только влево, верхней и правой сторонах.) |

**Название меню: состояние отключений**

![Название меню для инвалидов с глифом](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Название меню для инвалидов с глифом

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (текст) | `Environment.CommandBarTextInactive` |
| Передний план (глиф) | `Environment.CommandBarTextInactive` |
| Border | Отсутствуют |

#### <a name="menu-items"></a>Пункты меню
Отдельный пункт меню состоит из текста и необязательных значка, флажка или глифа подменю. Его цвета фона и текста меняются при наведении указателя. Этот токен цвета представляет собой пару, состоящую из цвета фона и цвета переднего плана.

![Красная линия пунктов меню](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Использовать... | Не используйте ... |
|---|---|
| ... для любого выпадающего списка, который запущен из панели меню или панели команд. | ... для любого выпадающего списка в другом контексте. |
| | ... в любом фоновом/переднем сочетании, кроме указанного. |

**Элементы меню: состояние по умолчанию**

![Элементы меню по умолчанию](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Элементы меню по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф подменю) | `Environment.CommandBarMenuSubmenuGlyph` |
| Border | `Environment.CommandBarMenuBorder` |
| Фон канала значка | `Environment.CommandBarMenuIconBackground` |
| Separator | `Environment.CommandBarMenuSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Элементы меню: проверенные и выбранные состояния**

![Меню с установленным флажком](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Проверенный пункт меню

![Выбранное меню](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Выбранный пункт меню

| Элемент | Имя токена: Category.color |
| --- | --- |
| Флажок | `Environment.CommandBarCheckBox` |
| Фон флажка | `Environment.CommandBarSelectedIcon` |
| Фон значка | `Environment.CommandBarSelected` |
| Граница значка | `Environment.CommandBarSelectedBorder` |

**Элементы меню: состояние нависки**

![Меню при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Пункт меню на нависке

![Меню при наведении курсора мыши с установленным флажком ](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Проверенный пункт меню на нависке

![Выбранное меню при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Выбранный пункт меню на нависке

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMenuItemMouseOver` |
| Передний план (текст) | `Environment.CommandBarMenuItemMouseOverText` |
| Передний план (глиф подменю) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Флажок | `Environment.CommandBarCheckBoxMouseOver` |
| Фон флажка | `Environment.CommandBarHoverOverSelectedIcon` |
| Фон значка | `Environment.CommandBarHoverOverSelected` |
| Граница значка | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Элементы меню: состояние отключений**

![Неактивное меню](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Пункт меню для инвалидов

![Неактивное меню с установленным флажком](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Отключенный пункт меню с чековой отметкой

| Элемент | Имя токена: Category.color |
| --- | --- |
| Передний план (текст) | `Environment.CommandBarTextInactive` |
| Передний план (глиф подменю) | `Environment.CommandBarMenuSubmenuGlyph` |
| Флажок | `Environment.CommandBarCheckBoxDisabled` |
| Фон флажка | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Командные бары
Панель команд может отображаться в нескольких местах в рамках Visual Studio IDE, в первую очередь на полке команд и встроенной в окна инструментов или документов.

Как правило, следует всегда использовать стандартную реализацию панели команд, предоставляемую средой Visual Studio. Использование стандартного механизма обеспечивает правильное отображение визуальных элементов и согласованное поведение интерактивных элементов и других элементов управления панели команд Visual Studio. Однако если вам необходимо создать собственную панель команд, следует правильно оформить ее с помощью указанных ниже имен токенов.

![Красная линия командной строки](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Командный бар (красная линия)

![Красная линия кнопки переполнения](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Кнопка переполнения (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... в местах, где вам нужна встроенная панель команд, но не удается использовать стандартную реализацию панели команд Visual Studio. | ... для элементов uI, которые не похожи на панель команд. |
| | ... для компонентов панели команд, кроме тех, для которых указаны имена маркеров. |

#### <a name="command-bar-groups"></a>Группы командных баров
Группа панели команд состоит из связанного набора элементов управления панели команд и может содержать любое количество кнопок, разворачивающихся кнопок, раскрывающихся меню, полей со списками или меню. Цвета этих элементов управления определяются отдельными именами токенов, которые рассматриваются в других частях этого руководства. Разделительная линия служит для разделения группы на панели команд в связанные подгруппы.

![Групповая красная линия командной строки](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Группа командного бара (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... в местах, где вам нужна встроенная панель команд, но не удается использовать стандартную реализацию панели команд Visual Studio. | ... для элементов uI, которые не похожи на панель команд. |
| | ... для компонентов панели команд, кроме тех, для которых указаны имена маркеров. |

**Группа панели команд: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarGradientBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Border | `Environment.CommandBarToolBarBorder` |
| Маркер перетаскивания | `Environment.CommandBarDragHandle` |
| Separator | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Значки команд
![Красная линия значка команды](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Значок команды (красная линия)

![Значок команды с красной строкой текста](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Значок команды с текстом (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... для любых кнопок, которые будут размещены на панели команд. | ... для элементов управления, которые имеют свои собственные имена маркеров. |
| | ... в любом фоновом/переднем сочетании, кроме указанного. |

**Значок команды: состояние по умолчанию**

![Значок команды по умолчанию](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Значок команды по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Н/Д (наследуется от фона панели команд) |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Border | Недоступно |

**Значок команды: состояние по умолчанию, выбранное**

![По умолчанию выбранный значок команды](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />По умолчанию выбранный значок команды

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarSelected` |
| Передний план (текст) | `Environment.CommandBarTextSelected` |
| Border | `Environment.CommandBarSelectedBorder` |

**Значок команды: нависшие или состояния фокусировки**

![Значок команды на нависении или фокусе](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Значок команды на нависении или фокусе

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Border | `Environment.CommandBarBorder` |

**Значок команды: нависает или фокус состояния, выбранные**

![Выбранный значок команды на нависении или фокусе](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Выбранный значок команды на нависении или фокусе

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarHoverOverSelected` |
| Передний план (текст) | `Environment.CommandBarTextHoverOverSelected` |
| Border | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Значок команды: нажатое состояние**

![Активный значок команды](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Активный значок команды

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.CommandBarTextMouseDown` |
| Border | `Environment.CommandBarBorder` |

**Значок команды: отключенное состояние**

![Неактивный значок команды](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Неактивный значок команды

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Н/Д (наследуется от фона панели команд) |
| Передний план (текст) | `Environment.CommandBarTextInactive` |
| Border | Недоступно |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a>Командный бар комбо коробки

> [!IMPORTANT]
> Поле со списком похоже на раскрывающийся список, но включает область для ввода и редактирования текста. Если выпадение не включает в себя область редактирования текста, используйте цветовые маркеры для [выпадения панели команд.](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)

![Команда бар комбо поле красной линии](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Командный бар комбо-бокс (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... при создании пользовательских комбо-коробок. | ... для чего-либо вы не хотите всегда соответствовать панели командный uI. |
| ... при создании управления панели команд, аналогичной комбо-коробке. | ... когда у вас есть доступ к стилизованной комбо-коробке. |

**Поле ввода комбо-панели команды: состояние по умолчанию**

![Поле ввода комбо-панели команды](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Поле ввода комбо-панели команды

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxBackground` |
| Передний план (текст) | `Environment.ComboBoxText` |
| Border | `Environment.ComboBoxBorder` |
| Separator | Без разделителя |

**Кнопка выпадения панели команд: состояние по умолчанию**

![Комбо окно падение&#45;вниз кнопку](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Кнопка выпадения панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Н/Д (наследуется от фона панели команд) |
| Передний план (глиф) | `Environment.ComboBoxGlyph` |

**Список выпадающих вниз командных баров: состояние по умолчанию**

![Список выпадающих командных баров](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Список выпадающих командных баров

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxPopupBackgroundBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.ComboBoxItemText` |
| Border | `Environment.ComboBoxPopupBorder` |

**Командная панель комбо поле ввода поле: состояние нависания**

![Командный бар комбо поле вхоточная поле на навешие](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Командный бар комбо поле вхоточная поле на навешие

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.ComboBoxMouseOverText` |
| Border | `Environment.ComboBoxMouseOverBorder` |
| Separator | `Environment.ComboBoxMouseOverSeparator` |

 **Кнопка выпадения панели команд: состояние навистого**

![Кнопка выпадения командного бара на нависнуть](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Кнопка выпадения командного бара на нависнуть

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxButtonMouseOverBackground` |
| Передний план (глиф) | `Environment.ComboBoxMouseOverGlyph` |

**Список выпадающих командных баров: состояние навистого**

 ![Командный бар выпадающий список на нависшие](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Командный бар выпадающий список на нависшие

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон (пункт меню) | `Environment.ComboBoxItemMouseOverBackground` |
| Передний план (текст) | `Environment.ComboBoxItemMouseOverText` |
| Граница (пункт меню) | `Environment.ComboBoxItemMouseOverBorder` |

 **Поле ввода комбо-панели команды: сфокусированное состояние**

![Целенаправленное поле ввода комбо-панели комбо-окна](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Целенаправленное поле ввода комбо-панели комбо-окна

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxFocusedBackground` |
| Передний план (текст) | `Environment.ComboBoxFocusedText` |
| Border | `Environment.ComboBoxFocusedBorder` |
| Separator | `Environment.ComboBoxFocusedButtonSeparator` |

**Кнопка выпадения панели команд: сфокусированное состояние**

![Кнопка сфокусированной кнопки выпадения панели команд](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Кнопка сфокусированной кнопки выпадения панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxFocusedButtonBackground` |
| Передний план (глиф) | `Environment.ComboBoxFocusedGlyph` |

 **Поле ввода комбо-панели команды: нажатое состояние**

![Прессованное поле комбо-коробки комбо-окна](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Прессованное поле комбо-коробки комбо-окна

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxMouseDownBackground` |
| Передний план (текст) | `Environment.ComboBoxMouseDownText` |
| Border | `Environment.ComboBoxMouseDownBorder` |
| Separator | `Environment.ComboBoxMouseDownSeparator` |

**Кнопка выпадения панели команд: нажатое состояние**

![Нажатие кнопки выпадения панели команд](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Нажатие кнопки выпадения панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxButtonMouseDownBackground` |
| Передний план (глиф) | `Environment.ComboBoxMouseDownGlyph` |

**Поле ввода комбо-панели команды: отключенное состояние**

![Отключено поле ввода комбо-панели комбо-панели команды](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Отключено поле ввода комбо-панели комбо-панели команды

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ComboBoxDisabledBackground` |
| Передний план (текст) | `Environment.ComboBoxDisabledText` |
| Border | `Environment.ComboBoxDisabledBorder` |
| Separator | Без разделителя |

**Кнопка выпадения панели команд: отключенное состояние**

![Отключена кнопка выпадения панели команд](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Отключена кнопка выпадения панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (глиф) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a>Падение командной панели

> [!IMPORTANT]
> Раскрывающийся список похож на поле со списком, но не имеет области для ввода и редактирования текста. Если выпадение включает в себя область редактирования текста, используйте цветовые маркеры для [комбо-коробок командной панели.](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)

![Выпадение панели команд (красная линия)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Выпадение панели команд (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... при создании пользовательских элементов управления списком выпадающих. | ... для всего, что не похоже на выпадающий список. |
| | ... для комбо-коробок или кнопок разделения. |

**Поле выбора панели команд: состояние по умолчанию**

![Поле выбора панели командного бара по умолчанию](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Поле выбора панели командного бара по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DropDownBackground` |
| Передний план (текст) | `DropDownText` |
| Border | `DropDownBorder` |
| Separator | Без разделителя |

**Кнопка выпадения панели команд: состояние по умолчанию**

![Кнопка выпадения панели команд по умолчанию](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Кнопка выпадения панели команд по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (глиф) | `Environment.DropDownGlyph` |

**Список выпадающих вниз командных баров: состояние по умолчанию**

![Список выпадающих вниз командных баров по умолчанию](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Список выпадающих вниз командных баров по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DropDownPopupBackgroundBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.ComboBoxItemText` |
| Border | `Environment.DropDownPopupBorder` |
| Shadow | `Environment.DropShadowBackground` |

**Поле выбора командной панели бара: состояние навистого**

![Командный бар выпадающих вниз выбор поле на нависшие](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Командный бар выпадающих вниз выбор поле на нависшие

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DropDownMouseOverBackgroundBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.DropDownMouseOverText` |
| Border | `Environment.DropDownMouseOverBorder` |
| Separator | `Environment.DropDownButtonMouseOverSeparator` |

**Кнопка выпадения панели команд: состояние навистого**

![Кнопка выпадения командного бара на нависнуть](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Кнопка выпадения командного бара на нависнуть

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DropDownButtonMouseOverBackground` |
| Передний план (глиф) | `Environment.DropDownMouseOverGlyph` |

**Список выпадающих командных баров: состояние навистого**

![Командный бар выпадающий список на нависшие](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Командный бар выпадающий список на нависшие

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон (пункт меню) | `Environment.ComboBoxItemMouseOverBackground` |
| Передний план (текст) | `Environment.ComboBoxItemMouseOverText` |
| Граница (пункт меню) | `Environment.ComboBoxItemMouseOverBorder` |

 **Поле выбора командной панели: нажатое состояние**

![Падение&#45;вниз по месту выбора нажата](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Нажатое поле выбора командной панели

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DropDownMouseDownBackground` |
| Передний план (текст) | `Environment.DropDownMouseDownText` |
| Border | `Environment.DropDownMouseDownBorder` |
| Separator | `Environment.DropDownButtonMouseDownSeparator` |

**Кнопка выпадения панели команд: нажатое состояние**

![Нажатие кнопки выпадения панели команд](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Нажатие кнопки выпадения панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DropDownButtonMouseDownBackground` |
| Передний план (глиф) | `Environment.DropDownMouseDownGlyph` |

**Поле выбора панели команд: состояние отключений**

![Отключено поле выбора панели командных выпадающих](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Отключено поле выбора панели командных выпадающих

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DropDownDisabledBackground` |
| Передний план (текст) | `Environment.DropDownDisabledText` |
| Border | `Environment.DropDownDisabledBorder` |
| Separator | Без разделителя |

**Кнопка выпадения панели команд: отключенное состояние**

![Отключена кнопка выпадения панели команд](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Отключена кнопка выпадения панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Недоступно |
| Передний план (глиф) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Кнопки разделения панели команд
Для разворачивающихся кнопок используются многие имена токенов, определенные для других элементов управления панели команд, таких как кнопки, меню и текст панели команд. Все необходимые имена токенов для действий и кнопок раскрывающихся списков приводятся здесь еще раз для удобства. Списки сплит-кнопок выпадают из списка - это реализации [меню командной панели.](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)

![Красная линия разворачивающейся кнопки](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Кнопка разделения панели команды (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... когда вы создаете пользовательскую кнопку разделения. | ... для других видов кнопок. |
| | ... в любом фоновом/переднем сочетании, кроме указанного. |

**Кнопка разделения панели команд: состояние по умолчанию**

![Кнопка разделения панели команд по умолчанию](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Кнопка разделения панели команд по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Отсутствуют |
| Передний план (текст) | `Environment.CommandBarTextActive` |
| Передний план (глиф) | `Environment.CommandBarSplitButtonGlyph` |
| Border | Недоступно |
| Separator | Недоступно |

**Кнопка разделения панели команды: состояние нависать**

![Кнопка разделения панели команды на нависнуть](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Кнопка разделения панели команды на нависнуть

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.CommandBarTextHover` |
| Передний план (глиф) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Border | `Environment.CommandBarBorder` |
| Separator | `Environment.CommandBarSplitButtonSeparator` |

**Кнопка разделения панели команды: нажатое состояние**

![Кнопка разделения панели команд](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Кнопка разделения панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.CommandBarTextMouseDown` |
| Передний план (глиф) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Border | `Environment.CommandBarBorder` |
| Separator | Недоступно |

**Кнопка разделения панели команды: отключенное состояние**

![Отключенная кнопка разделения панели команд](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Отключенная кнопка разделения панели команд

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Недоступно |
| Передний план (текст) | `Environment.ComboBoxItemTextInactive` |
| Передний план (глиф) | `Environment.CommandBarTextInactive` |
| Border | Недоступно |
| Separator | Недоступно |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Кнопки «Больше вариантов» и «Перелив»
Кнопка "Дополнительно" используется, если группа панели команд может настраиваться путем добавления или удаления связанных кнопок. Кнопка "Переполнение" появляется, если панель команд усекается из-за отсутствия места по горизонтали. При ее нажатии открывается меню, содержащее кнопки, которые не поместились на панели команд. Цвета этих двух кнопок определяются одним и тем же набором имен токенов.

![Кнопка «Больше вариантов» (красная линия)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Кнопка «Больше вариантов» (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... для пользовательских кнопок «Больше опций» или «Перелив». | ... для кнопок, не имеюх аналогичной функциональности с кнопкой «Больше опций» или «Перелив». |

**Кнопки «Больше вариантов» и «Перелив»: состояние по умолчанию**

![Кнопка панели команд по умолчанию 'Больше опций'](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Кнопка панели команд по умолчанию 'Больше опций'

![Кнопка панели команд по умолчанию 'Overflow'](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Кнопка панели команд по умолчанию 'Overflow'

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarOptionsBackground` |
| Передний план (глиф) | `Environment.CommandBarOptionsGlyph` |

**Кнопки командного бара «Больше вариантов» и «Перелив»: состояние навистого**

![Кнопка командного бара 'Больше вариантов' на нависнуть](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Кнопка командного бара 'Больше вариантов' на нависнуть

![Кнопка командного бара 'Переполнение' на нависнуть](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Кнопка командного бара 'Переполнение' на нависнуть

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (глиф) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Кнопки командного бара «Больше вариантов» и «Перелив»: нажатое состояние**

![Нажатие кнопки "Больше опций"](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Нажатие кнопки "Больше опций"

![Активное переполнение](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Нажатие кнопки "Перелив" панели

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (глиф) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Окна документов
Нет необходимости воспроизводить окна документов, поскольку они предоставляются средой Visual Studio. Однако может потребоваться использовать цвета, применяемые в окнах документов, чтобы ваш пользовательский интерфейс был согласован с этой частью среды Visual Studio.

При использовании цветовых токенов оконного окна, будьте осторожны, чтобы использовать их только для аналогичных элементов, и всегда в парах. Если вы этого не сделаете, вы можете получить неожиданные результаты в вашем uI.

### <a name="document-window-frames"></a>Кадры окна документов
Окна документов могут быть закрепленными в интегрированной среде разработки или перемещаемыми как отдельные окна. Когда окно документа плавает за пределами IDE, оно по-прежнему хорошо сидит в документе и имеет фон, границу, текст и цвета вкладок, которые такие же, как когда он является частью IDE. Однако документ размещается внутри рамки, которая имеет собственные цвета фона, границы и текста. Если в контейнере документа закреплены окна инструментов, они наследуют поведение и цвет вкладок от имен токенов окна документа.

![Окно священного документа (красная линия)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Окно священного документа (красная линия)

![Плавающее окно документа (красная линия)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Плавающее окно документа (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... где бы вы ни создавали ui, который требуется сопоставить с окном документа. | ...  для любого uI, который вы не хотите автоматически менять, если оболочка имеет обновление темы. |

**Пристыковано ею или плавающее окно документа: состояние по умолчанию**

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Зависит от типа документа |
| Передний план (текст) | Зависит от типа документа |
| Border | `Environment.ToolWindowBorder` |

**Сфокусированная, плавающая оконная рамка документа: состояние по умолчанию**

![Сфокусированная по умолчанию, плавающая оконная рама документов](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Сфокусированная по умолчанию, плавающая оконная рама документов

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowFloatingFrame` |
| Передний план (текст) | `Environment.ToolWindowFloatingFrame` |
| Передний план (глиф) | `Environment.RaftedWindowButtonActiveGlyph` |
| Border | `Environment.MainWindowActiveDefaultBorder` |
| Граница (глиф) | `Environment.RaftedWindowButtonActiveBorder`<br />(Установить прозрачный) |

**Нефокусированный, плавающий оконный каркас документа: состояние по умолчанию**

![Нефокусированный по умолчанию, плавающая оконная рамка документа](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Нефокусированный по умолчанию, плавающая оконная рамка документа

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowFloatingFrameInactive` |
| Передний план (текст) | `Environment.ToolWindowFloatingFrameInactive` |
| Передний план (глиф) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Border | `Environment.MainWindowInactiveBorder` |
| Граница (глиф) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Установить прозрачный) |

**Сфокусированная, плавающая оконная рама документа: состояние нависания**

![Сфокусированная, плавающая оконная рама документа на нависке](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Сфокусированная, плавающая оконная рама документа на нависке

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон (глиф) | `Environment.RaftedWindowButtonHoverActive` |
| Передний план (глиф) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Граница (глиф) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Нефокусированный, плавающий оконный каркас документа: состояние нависания**

![Нефокусированный, плавающий документ оконной рамы на нависает](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Нефокусированный, плавающий документ оконной рамы на нависает

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон (глиф) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Передний план (глиф) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Граница (глиф) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Сфокусированная, плавающая оконная рама документа: нажатое состояние**

![Плавающая, плавающая оконная рамка документов на прессе](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Плавающая, плавающая оконная рамка документов на прессе

| Элемент | Имя токена: Category.color |
| --- | --- |
| Фон (глиф) | `Environment.RaftedWindowButtonDown` |
| Передний план (глиф) | `Environment.RaftedWindowButtonDownGlyph` |
| Граница (глиф) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Вкладки документов
Вкладки документов размещаются в канале вкладок и указывают, какие документы в настоящее время открыты, а также какой документ в настоящий момент выбран или активен. Окна инструментов также могут закрепляться в канале вкладок документов, если пользователь размещает их там. В этом случае для них используются те же цвета, что и для окон документов. Если вы создаете пользовательский интерфейс, цвета которого должны всегда соответствовать цветам окна документа (в том числе при обновлении темы или установке новых тем), то используйте ссылки на указанные ниже токены цветов.

![Вкладки документов (красная линия)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Вкладки документов (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... везде, где вы создаете uI, который вы хотите сопоставить вкладки документов и автоматически подобрать обновления темы или новые цвета темы. | ... для любого uI, который вы не хотите менять автоматически, когда оболочка имеет обновление темы. |

#### <a name="open-document-tabs"></a>Вкладки открытых документов
Каждый открытый документ имеет вкладку в канале вкладок документов, на которой показано его имя. Документы могут быть либо выбраны, либо открыты в фоновом режиме. На их вкладках указываются перечисленные ниже состояния.

- Выбранная вкладка представляет документ, который в настоящее время отображается в контейнере документа. Выбранная вкладка имеет границу документа, которая располагается по верхнему краю контейнера документа.

- Фоновые вкладки представляют любые вкладки документов, которые не являются выбранной в настоящее время вкладкой. После нажатия они становятся выбранной вкладкой и приобретают все фоновые, пограничные и текстовые цвета из этих имен маркеров.

![Открытая вкладка документа (красная линия)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Открытая вкладка документа (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... при создании пользовательских вкладок документа. | ... для предварительных (предварительных) вкладок. |
| | ... для любого uI, который вы не хотите менять автоматически, если оболочка имеет обновление темы. |

**Выбранная, сфокусированная вкладка документа**

![Выбранная, сфокусированная вкладка документа](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Выбранная, сфокусированная вкладка документа

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabSelectedGradientTop`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.FileTabSelectedText` |
| Border | `Environment.FileTabSelectedBorder`<br />(Установить тот же цвет, что и фон.) |
| Граница документа | `Environment.FileTabDocumentBorderBackground` |

**Выбранная, нефокусированная вкладка документа**

![Выбранная, нефокусированная вкладка документа](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Выбранная, нефокусированная вкладка документа

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabInactiveGradientTop`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.FileTabInactiveText` |
| Border | `Environment.FileTabInactiveBorder`<br />(Установить тот же цвет, что и фон.) |
| Граница документа | `Environment.FileTabInactiveDocumentBorderBackground` |

**Вкладка фонового документа: состояние по умолчанию**

![Вкладка фонового документа по умолчанию](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Вкладка фонового документа по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabBackground` |
| Передний план (текст) | `Environment.FileTabText` |
| Border | `Environment.FileTabBorder`<br />(Установить тот же цвет, что и фон.) |

**Вкладка фонового документа: состояние навистого**

![Вкладка фонового документа на нависке](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Вкладка фонового документа на нависке

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabHotGradientTop`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.FileTabHotText` |
| Border | `Environment.FileTabHotBorder`<br />(Установить тот же цвет, что и фон.) |

#### <a name="preview-tab"></a>Вкладка предварительного просмотра
Также называется "временной" вкладке. Вкладка предварительного просмотра отображается на правой стороне канала вкладки документа, когда пользователь нажимает на элемент в окне инструмента Solution Explorer. Она служит для предварительного просмотра документа и дает пользователю возможность сохранять документ открытым в левой части канала вкладок документов. Одновременно может быть открыта только одна вкладка предварительного просмотра. Так же как открытые вкладки, вкладки предварительного просмотра имеют как фоновое, так и выбранное состояния и в активном состоянии могут получать фокус ввода и терять его.

![Вкладка предварительного просмотра (красная линия)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Вкладка предварительного просмотра (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... где бы вы ни создавали предварительный предварительный просмотр и хотите, чтобы какой-то элемент соответствовал текущему цвету вкладки предварительного просмотра. | ... для любого документа или вкладки, которая не является временной (предварительный просмотр). |
| | ... для любого uI, который вы не хотите менять автоматически, если оболочка имеет обновление темы. |

**Сфокусированная, выбранная вкладка предварительного просмотра**

![Сфокусированная, выбранная вкладка предварительного просмотра](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Сфокусированная, выбранная вкладка предварительного просмотра

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabProvisionalSelectedActive` |
| Передний план (текст) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Border | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Установить тот же цвет, что и фон.) |
| Граница документа | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Нефокусированная, выбранная вкладка предварительного просмотра**

![Нефокусированная, выбранная вкладка предварительного просмотра](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Нефокусированная, выбранная вкладка предварительного просмотра

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabProvisionalSelectedInactive` |
| Передний план (текст) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Border | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Граница документа | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Вкладка предварительного просмотра: состояние по умолчанию**

![Вкладка фонового предварительного просмотра по умолчанию](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Вкладка фонового предварительного просмотра по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabProvisionalInactive` |
| Передний план (текст) | `Environment.FileTabProvisionalInactiveForeground` |
| Border | `Environment.FileTabProvisionalInactiveBorder`<br />(Установить тот же цвет, что и фон.) |

**Вкладка предварительного просмотра фона: состояние навистого**

![Вкладка предварительного просмотра фона на нависе](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Вкладка предварительного просмотра фона на нависе

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.FileTabProvisionalHover` |
| Передний план (текст) | `Environment.FileTabProvisionalHoverForeground` |
| Border | `Environment.FileTabProvisionalHoverBorder`<br />(Установить тот же цвет, что и фон.) |

#### <a name="document-overflow-button"></a>Кнопка переполнения документа
Кнопка переполнения документа присутствует, если открыт один или несколько документов, вне зависимости от того, имеется ли в текущей конфигурации пространство по вертикали для размещения всех вкладок документов. Меню переполнения документа, которое контролируется цветами [меню меню командной панели,](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) отображает список всех открытых документов, как видимых, так и скрытых, а перелив глифа изменяется в зависимости от того, отображаются ли все открытые документы в канале вкладок.

![Кнопка переполнения документов (красная линия)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Кнопка переполнения документов (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... при создании кнопки переполнения пользовательского документа. | ... для uI, который не похож на кнопку переполнения. |
| | ... для кнопок переполнения панели команд. |

**Кнопка переполнения документов: состояние по умолчанию**

![Кнопка переполнения документов по умолчанию](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Кнопка переполнения документов по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DocWellOverflowButtonBackground` |
| Передний план (глиф) | `Environment.DocWellOverflowButtonGlyph` |
| Border | Недоступно |

**Кнопка переполнения документов: состояние нависав**

![Кнопка переполнения документа при наведении указателя](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Кнопка переполнения документа при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Передний план (глиф) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Border | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Кнопка переполнения документов: нажатое состояние**

![Кнопка переполнения документов на нажатии](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Кнопка переполнения документов на нажатии

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Передний план (глиф) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Border | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Добавление тегов
Visual Studio поддерживает добавление тегов, что позволяет пользователю объявлять доступные для поиска ключевые слова в целях отслеживания. Например, руководители проектов и разработчики могут использовать Team Foundation Server (TFS) для добавления тегов к рабочим элементам. В приведенных ниже таблицах представлены имена цветов как для самого тега, так и для глифа (значка закрытия), который появляется при наведении указателя и в некоторых состояниях.

![Метки в визуальной студии (красная линия)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Метки в визуальной студии (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... для uI, поддерживающего пометку. | ... для любого другого типа uI. |

#### <a name="tags"></a>Теги

**Тег: Состояние по умолчанию**

![Тег по умолчанию](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Тег по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.Background` |
| Передний план (текст) | `Tag.Background` |

**Тег: состояние навистого**

![Тег при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Тег при наведении указателя мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.HoverBackground` |
| Передний план (текст) | `Tag.HoverBackgroundText` |

**Тег: нажатое состояние**

![Нажатый тег](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Нажатый тег

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.PressedBackground` |
| Передний план (текст) | `Tag.PressedBackgroundText` |

**Тег: выбранное состояние**

![Выбранный тег](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Выбранный тег

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.SelectedBackground` |
| Передний план (текст) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Закрыть&times;() тег глифа

**Закрыть&times;() тег глифа: состояние по умолчанию**

![По умолчанию Закрыть (&times;) тегглиф](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />По умолчанию Закрыть (&times;) тегглиф

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Недоступно |
| Передний план (глиф) | `Tag.TagHoverGlyph` |

**Закрыть&times;() тегглифа: состояние навистого**

![Закрыть&times;( ) тегглифа на нависшие](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Закрыть&times;( ) тегглифа на нависшие

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.TagHoverGlyphHoverBackground` |
| Передний план (глиф) | `Tag.TagHoverGlyphHover` |
| Border | `Tag.TagHoverGlyphHoverBorder` |

**Закрыть&times;() тег глифа: нажатое состояние**

![Прессованные Закрыть (&times;) тегглиф](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Прессованные Закрыть (&times;) тегглиф

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.TagHoverGlyphPressedBackground` |
| Передний план (глиф) | `Tag.TagHoverGlyphPressed` |
| Border | `Tag.TagHoverGlyphPressedBorder` |

**Выбранный тег с&times;close ( ) глиф: состояние по умолчанию**

![По умолчанию выбранный&times;тег с закрытием ( ) глиф](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />По умолчанию выбранный&times;тег с закрытием ( ) глиф

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Недоступно |
| Передний план (глиф) | `Tag.TagSelectedGlyph` |

**Выбранный тег с&times;близко () глиф: состояние нависать**

![Выбранный тег с&times;близко () глиф на навешить](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Выбранный тег с&times;близко () глиф на навешить

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.TagSelectedGlyphHoverBackground` |
| Передний план (глиф) | `Tag.TagSelectedGlyphHover` |
| Border | `Tag.TagSelectedGlyphHoverBorder` |

**Выбранный тег с&times;близко () глиф: нажатое состояние**

![Выбранный, нажатый&times;тег с закрыть ( ) глиф](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Выбранный, нажатый&times;тег с закрыть ( ) глиф

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Tag.TagSelectedGlyphPressedBackground` |
| Передний план (глиф) | `Tag.TagSelectedGlyphPressed` |
| Border | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Окна инструментов
Нет необходимости реплицировать окна инструментов, потому что они предоставляются средой Visual Studio. Однако может потребоваться использовать цвета, применяемые в окнах инструментов, чтобы ваш пользовательский интерфейс был согласован с этой частью среды Visual Studio.

![Окно инструмента (красная линия)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Окно инструмента (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... везде, где вы создаете uI, который вы хотите сопоставить окна инструментов. | ... для любого uI, который вы не хотите менять автоматически, если оболочка имеет обновление темы. |

### <a name="tool-window-frame"></a>Рамка окна инструментов
Окна инструментов в Visual Studio используются для множества различных задач и могут иметь одно из нескольких состояний. Если окно инструментов открыто, оно может быть назначено одной из четырех сторон области документа. Окна инструментов также могут перемещаться за пределы интегрированной среды документов, что позволяет размещать их в любом месте экрана. Перемещаемые окна всегда находятся поверх интегрированной среды разработки. Наконец, окна инструментов могут закрепляться как окна документов и отображаться в виде вкладок в контейнере документа. К окнам инструментов, закрепленным как окна документов, частично применяются имена токенов окна документа.

![Рамка окна инструмента (красная линия)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Рамка окна инструмента (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ...  везде, где вы создаете uI, который вы хотите сопоставить окна инструментов. | ... для любого uI, который вы не хотите менять автоматически, если оболочка имеет обновление темы. |

**Окно стыковки с инструментами**

![Окно стыковки с инструментами](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Окно стыковки с инструментами

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowBackground` |
| Border | `Environment.ToolWindowBorder` |

**Плавающее, сфокусированное окно инструмента**

![Плавающее, сфокусированное окно инструмента](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Плавающее, сфокусированное окно инструмента

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowBackground` |
| Border | `Environment.MainWindowActiveDefaultBorder` |

**Плавающее, нефокусированное окно инструмента**

![Плавающее, нефокусированное окно инструмента](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Плавающее, нефокусированное окно инструмента

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowBackground` |
| Border | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Окна, похожие на инструменты
Набор инструментов является одним из наиболее часто используемых обычных окон инструментов в Visual Studio. Это по существу управление деревом с особой темой и укладка применяется.

![Toolbox-подобное окно (красная линия)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Toolbox-подобное окно (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... при проектировании окна инструментов, которое вы хотите всегда согласовывать с набором инструментов оболочки. | ... для всего, что не похоже на uI-образного ввоза инструментария, или если вы не уверены, возникнет ли у вашего uI проблем, если изменятся цвета панели инструментов оболочки. |

**Узлы Toolbox: состояние по умолчанию**

![Родительский узла по умолчанию](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Родительский узла по умолчанию

![Детский узла по умолчанию](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Детский узла по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolboxContent`<br />(Заголовки) |
| Историческая справка | `Environment.ToolWindowBackground`<br />(Индивидуальные элементы, или все окно, если нет доступных элементов управления) |
| Border | Отсутствуют |
| Передний план (глиф) | `Environment.ToolboxContent` |
| Передний план (текст) | `Environment.ToolboxContent` |

**Детские узлы Toolbox: состояние навистого**

![Дочерний узел панели инструментов при наведении указателя мыши](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Дочерний узел панели инструментов при наведении указателя мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolboxContentMouseOver`<br />(Только отдельные предметы) |
| Border | Отсутствуют |
| Передний план (текст) | `Environment.ToolboxContentMouseOver`<br />(Только отдельные предметы) |

**Выбранные узлы наборов инструментов: сфокусированное состояние**

![Выбранный родительский узла набор инструментов](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Выбранный родительский узла набор инструментов

![Выбранный детский узла ящика инструментов](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Выбранный детский узла ящика инструментов

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemActive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Border | `TreeView.FocusVisualBorder`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Передний план (глиф) | `TreeView.SelectedItemActive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Передний план (текст) | `TreeView.SelectedItemActive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Выбранные узлы наборов инструментов: нефокусированное состояние**

![Выбранный, нефокусированный родительский узла из инструментария](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Выбранный, нефокусированный родительский узла из инструментария

![Выбранный, нефокусированный детский узла ящика инструментов](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Выбранный, нефокусированный детский узла ящика инструментов

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `TreeView.SelectedItemInactive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Border | Отсутствуют |
| Передний план (глиф) | `TreeView.SelectedItemInactive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Передний план (текст) | `TreeView.SelectedItemInactive`<br />Из категории [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Заголовок окна инструментов
Граница заголовок бара не является истинной границей, это толстая линия в верхней части заголовка бара. Он не имеет символического названия для своего нефокусированного состояния.

![Панель заголовка окна инструмента (красная линия)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Панель заголовка окна инструмента (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... везде, где вы создаете uI, который вы хотите сопоставить окна инструментов. | ... для любого uI, который вы не хотите менять автоматически, если оболочка имеет обновление темы. |

**Заголовок окна с фокусом ввода**

![Заголовок окна с фокусом ввода](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Заголовок окна с фокусом ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.TitleBarActiveGradientBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.TitleBarActiveText` |
| Border | `Environment.TitleBarActiveBorder`<br />(Установить тот же цвет, что и фон.) |
| Маркер перетаскивания | `Environment.TitleBarDragHandleActive` |

**Заголовок окна без фокуса ввода**

![Панель заголовка без фокуса ввода](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Заголовок окна без фокуса ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.TitleBarInactiveGradientBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.TitleBarInactiveText` |
| Border | Недоступно |
| Маркер перетаскивания | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Кнопки заголовка заголовка окна инструмента
![Кнопка заголовка (красная линия)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Кнопка заголовка (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... для кнопок, которые отображаются в uI, использующем цветовые маркеры из баров заголовка окна инструмента. | ... для кнопок, которые появляются в других местах. |
| | ... в любом фоновом/переднем сочетании, кроме указанного. |

**Кнопки сфокусированной панели заголовков: состояние по умолчанию**

![По умолчанию, сфокусированные кнопки заголовка](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />По умолчанию, сфокусированные кнопки заголовка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Недоступно |
| Передний план (глиф) | `Environment.ToolWindowButtonActiveGlyph` |
| Border | Недоступно |

**Нефокусированные кнопки заголовка: состояние по умолчанию**

![По умолчанию, нефокусированные кнопки заголовка](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />По умолчанию, нефокусированные кнопки заголовка

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | Недоступно |
| Передний план (глиф) | `Environment.ToolWindowButtonInactiveGlyph` |
| Border | Недоступно |

**Кнопки сфокусированной заглавной панели: состояние нависать**

![Кнопки заголовка бар на нависает](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Кнопки заголовка бар на нависает

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowButtonHoverActive` |
| Передний план (глиф) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Border | `Environment.ToolWindowButtonHoverActiveBorder` |

**Нефокусированные кнопки заголовка: состояние навистого**

![Нефокусированные кнопки заголовка бар на нависнуть](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Нефокусированные кнопки заголовка бар на нависнуть

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowButtonHoverInactive` |
| Передний план (глиф) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Border | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Кнопки сфокусированной панели заголовка: нажатое состояние**

![Кнопки заголовка на нажатии](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Кнопки заголовка на нажатии

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowButtonDown` |
| Передний план (глиф) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Border | `Environment.ToolWindowButtonDownBorder` |

**Кнопки несфокусированной панели заголовка: нажатое состояние**

![Нефокусированные кнопки заголовка на прессе](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Нефокусированные кнопки заголовка на прессе

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowButtonDown` |
| Передний план (глиф) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Border | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Вкладки окна инструментов
![Вкладка окна инструмента (красная линия)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Вкладка окна инструмента (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... везде, где вы создаете uI, который вы хотите сопоставить окна инструментов. | ... для любого uI, который вы не хотите менять автоматически, если оболочка имеет обновление темы. |

**Выбранная вкладка окна инструментов с фокусом ввода**

![Выбранная вкладка окна инструментов с фокусом ввода](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Выбранная вкладка окна инструментов с фокусом ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowTabSelectedTab` |
| Передний план (текст) | `Environment.ToolWindowTabSelectedActiveText` |
| Border | `Environment.ToolWindowTabSelectedBorder`<br />(Установить тот же цвет, что и фон.) |

**Выбранная вкладка окна инструментов без фокуса ввода**

![Выбранная вкладка окна инструментов без фокуса ввода](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Выбранная вкладка окна инструментов без фокуса ввода

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowTabSelectedTab` |
| Передний план (текст) | `Environment.ToolWindowTabSelectedText` |
| Border | `Environment.ToolWindowTabSelectedBorder`<br />(Установить тот же цвет, что и фон.) |

**Вкладка окна фонового инструмента: состояние по умолчанию**

![Вкладка окна фонового инструмента по умолчанию](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Вкладка окна фонового инструмента по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Gradient останавливается, установленный на то же значение цвета в Visual Studio 2013.) |
| Передний план (текст) | `Environment.ToolWindowTabText` |
| Border | `Environment.ToolWindowTabBorder` |

**Вкладка окна фонового инструмента: состояние навистого**

![Фоновая вкладка окна инструментов при наведении указателя](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Фоновая вкладка окна инструментов при наведении указателя

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Gradient останавливается, установленный на то же значение цвета в Visual Studio 2013.) |
| Передний план (текст) | `Environment.ToolWindowTabMouseOverText` |
| Border | `Environment.ToolWindowTabMouseOverBorder`<br />(Установить тот же цвет, что и фон.) |

### <a name="auto-hide-tabs"></a>Автоматически скрываемые вкладки

![Вкладки автоматической скрытия (красная линия)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") Вкладки автоматической скрытия (красная линия)

| Использовать... | Не используйте ... |
| --- | --- |
| ... везде, где вы создаете uI, который вы хотите, чтобы соответствовать автоматически скрытые вкладки окна инструмента. | ... для любого uI, который вы не хотите менять автоматически, если оболочка имеет обновление темы. |

**Вкладки автоматического сокрытия: состояние по умолчанию**

![Автоматически скрываемая вкладка по умолчанию](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Автоматически скрываемая вкладка по умолчанию

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.AutoHideTabBackgroundBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.AutoHideTabText` |
| Border | `Environment.AutoHideTabBorder` |

**Авто-скрыть вкладки: состояние нависать**

![Вкладка автоматического скрытия при наведении курсора мыши](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Вкладка автоматического скрытия при наведении курсора мыши

| Элемент | Имя токена: Category.color |
| --- | --- |
| Историческая справка | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Градиентные остановки для этого маркера, не используемого в тематиченном uI.) |
| Передний план (текст) | `Environment.AutoHideTabMouseOverText` |
| Border | `Environment.AutoHideTabMouseOverBorder` |
