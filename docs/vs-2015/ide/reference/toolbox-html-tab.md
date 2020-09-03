---
title: Вкладка "HTML", панель элементов | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4474f2a0823b5599da30706daedff6e5cd1fc0f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851660"
---
# <a name="toolbox-html-tab"></a>Вкладка HTML, панель элементов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Вкладка **HTML** панели элементов предоставляет компоненты, которые полезны для использования на веб-страницах и веб-формах. Для просмотра этой вкладки сначала откройте HTML-документ в конструкторе HTML. В меню **Вид** щелкните **Панель элементов** и откройте вкладку **HTML** на панели элементов.

 Для создания экземпляра средства на вкладке **HTML** дважды щелкните средство, чтобы добавить его в документ в текущем положении курсора, или выберите средство и перетащите его в нужное место на поверхности редактирования.

## <a name="tasks"></a>Задания

- [Практическое руководство. Управление окном панели элементов](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)

- [Практическое руководство. Управление вкладками панели элементов](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db)

## <a name="ui-elements"></a>Элементы пользовательского интерфейса
 По умолчанию на вкладке HTML доступны указанные ниже средства.

 **Указатель** ![ASP.NET мобильного конструктора HtmlPage указатель](../../ide/reference/media/vxpointer.gif "вкспоинтер")

 Это средство выбирается по умолчанию при открытии любой вкладки области элементов. Его нельзя удалить. Указатель позволяет перетаскивать объекты на поверхность конструктора, изменять их размеры и перемещать по странице или форме. Дополнительные сведения см. в разделах [Практическое руководство. Управление окном панели элементов](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) и [Практическое руководство. Управление вкладками панели элементов](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 Кнопка **ввода (кнопка)** ![HTML веб-страница](../../ide/reference/media/vxbutton.gif "вксбуттон")

 Вставляет элемент `input` объекта `type="button"`. Чтобы изменить отображаемый текст, измените свойство `name`. По умолчанию `id="Button1"` вставляется для первой кнопки, `id="Button2"` для второй и т. д.

 Когда вы перетаскиваете элемент **Ввод (кнопка)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:

```
<input id="Button1" type="button" value="Button" name="Button1">
```

 Дополнительные сведения см. в статьях [HTML Input Controls](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) (Элементы управления для ввода HTML), [Декларативный синтаксис серверного элемента управления HtmlInputButton](https://msdn.microsoft.com/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [How to: Create Scripts and Edit Event Handlers](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d) (Руководство по созданию скриптов и редактированию обработчиков событий), [Button Web Server Controls Content Map](https://msdn.microsoft.com/library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf) (Обзор элементов управления веб-сервера Button), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton> и <xref:System.Web.UI.WebControls.Button>.

 ![Снимок экрана](../../ide/reference/media/vxreset.gif "вксресет") **ввода (сброса)** снимок

 Вставляет элемент `input` объекта `type="reset"`. Чтобы изменить отображаемый текст, измените свойство `name`. По умолчанию `id="Reset1"` вставляется для первой кнопки сброса, `id="Reset2"` для второй и т. д.

 Когда вы перетаскиваете элемент **Ввод (кнопка сброса)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:

```
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

 Дополнительные сведения см. в статьях [HTML Input Controls](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) (Элементы управления для ввода HTML), [Декларативный синтаксис серверного веб-элемента управления HtmlInputReset](https://msdn.microsoft.com/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton> и <xref:System.Web.UI.WebControls.Button>.

 ![Снимок экрана](../../ide/reference/media/vxsubmit.gif "вкссубмит") **ввода (отправка)** снимок

 Вставляет элемент `input` объекта `type="submit"`. Чтобы изменить отображаемый текст, измените свойство `name`. По умолчанию `id="Submit1"` вставляется для первой кнопки отправки, `id="Submit2"` для второй и т. д.

 Когда вы перетаскиваете элемент **Ввод (кнопка отправки)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:

```
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

 Дополнительные сведения см. в статьях [HTML Input Controls](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) (Элементы управления для ввода HTML), [Декларативный синтаксис серверного элемента управления HtmlInputSubmit](https://msdn.microsoft.com/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton> и <xref:System.Web.UI.WebControls.Button>.

 ![Снимок экрана](../../ide/reference/media/vxtextfield.gif "вкстекстфиелд") **ввода (текста)** HTMLpageToolbarTextField

 Вставляет элемент `input` объекта `type="text"` в документ. Чтобы изменить отображаемый текст по умолчанию, измените атрибут `value`. По умолчанию `id="Text1"` вставляется для первого текстового поля, `id="Text2"` для второго и т. д.

 Когда вы перетаскиваете элемент **Ввод (текст)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:

```
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

 Дополнительные сведения см. в статьях [HTML Input Controls](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) (Элементы управления для ввода HTML), [Декларативный синтаксис серверного веб-элемента управления HtmlInputText](https://msdn.microsoft.com/87060d90-a11c-434d-9fc9-b03a8487041e), [TextBox Web Server Control Overview](https://msdn.microsoft.com/library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f) (Обзор элемента управления веб-сервера TextBox), <xref:System.Web.UI.HtmlControls.HtmlInputText> и <xref:System.Web.UI.WebControls.TextBox>.

> [!IMPORTANT]
> Рекомендуется проверить весь пользовательский ввод. Дополнительные сведения см. в разделе [Проверка пользовательского ввода на веб-страницах ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 ![Поле файла HTML-страницы](../../ide/reference/media/vxfilefield.gif "вксфилефиелд") **ввода (файла)**

 Вставляет элемент `input` объекта `type="file"` в документ. По умолчанию `id="File1"` вставляется для первого поля файла, `id="File2"` для второго и т. д.

 Когда вы перетаскиваете элемент **Ввод (файл)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:

```
<input id="File1" type="file" name="File1">
```

 Дополнительные сведения см. в статьях [HTML Input Controls](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) (Элементы управления для ввода HTML), [Декларативный синтаксис серверного веб-элемента управления HtmlInputFile](https://msdn.microsoft.com/a817b4a0-056f-4c17-a696-b9fdcde43db6) и <xref:System.Web.UI.HtmlControls.HtmlInputFile>.

> [!IMPORTANT]
> Рекомендуется проверить весь пользовательский ввод. Дополнительные сведения см. в разделе [Проверка пользовательского ввода на веб-страницах ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 Поле **ввода пароля (пароль)** ![Visual Studio](../../ide/reference/media/vxpassword.gif "вкспассворд")

 Вставляет элемент `input` объекта `type="password"`. По умолчанию `id="Password1"` вставляется для первого поля пароля, `id="Password2"` для второго и т. д.

 Когда вы перетаскиваете элемент **Ввод (пароль)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:

```
<input id="Password1" type="password" name="Password1">
```

 Дополнительные сведения см. в разделе [Элементы управления ввода HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Декларативный синтаксис серверного элемента управления HtmlInputPassword](https://msdn.microsoft.com/df703dd0-1624-4e5a-a547-c97f2f331b9f), [Практическое руководство. Установка серверного веб-элемента управления для ввода пароля](https://msdn.microsoft.com/library/5b5069f3-64a1-435a-aee6-da263f4e6310) и [Практическое руководство. Проверка пользовательского ввода на странице веб-форм](https://msdn.microsoft.com/library/7141d6ba-34f3-410b-b5cd-2102a24cb436).

> [!IMPORTANT]
> Если приложение передает имена пользователей и пароли, следует настроить веб-сайт, чтобы использовать SSL для шифрования передачи. Подробнее см. в подразделе "Обеспечение безопасности подключений с помощью SSL" раздела [Руководство по операциям IIS](https://technet.microsoft.com/library/cc732976(v=WS.10).aspx). Дополнительно рекомендуется проверить весь пользовательский ввод. Дополнительные сведения см. в разделе [Проверка пользовательского ввода на веб-страницах ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 **Ввод (флажок)** ![параметр "Панель элементов веб-страницы HTML"](../../ide/reference/media/vxcheckbox.gif "вксчеккбокс")

 Вставляет элемент `input` объекта `type="checkbox"`. Чтобы изменить отображаемый текст, измените свойство `name`. По умолчанию `id="Checkbox1"` вставляется для первого флажка, `id="Checkbox2"` для второго и т. д.

 Когда вы перетаскиваете элемент **Ввод (флажок)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:

```
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

 Дополнительные сведения см. в статьях [HTML Input Controls](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) (Элементы управления для ввода HTML), [Декларативный синтаксис серверного элемента управления HtmlInputCheckBox](https://msdn.microsoft.com/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [CheckBox and CheckBoxList Web Server Controls Overview](https://msdn.microsoft.com/library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf) (Обзор элементов управления веб-сервера CheckBox и CheckBoxList), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox> и <xref:System.Web.UI.WebControls.CheckBox>.

 ![Снимок экрана](../../ide/reference/media/vxradio.gif "вксрадио") **входного (радио)** VisualStudioHTMLpageRadioButton

 Вставляет элемент `input` объекта `type="radio"`. Чтобы изменить отображаемый текст, измените свойство `name`. По умолчанию `id="Radio1"` вставляется для первого переключателя, `id="Radio2"` для второго и т. д.

 Когда вы перетаскиваете элемент **Ввод (переключатель)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:

```
<input id="Radio1" type="radio" name="Radio1">
```

 Дополнительные сведения см. в статьях [HTML Input Controls](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) (Элементы управления для ввода HTML), [Декларативный синтаксис серверного элемента управления HtmlInputRadioButton](https://msdn.microsoft.com/6e60ff63-cc57-46ef-bf96-e829e204ba33), [RadioButton and RadioButtonList Web Server Controls Overview](https://msdn.microsoft.com/library/20eb383c-4b59-432b-bba3-e9d785107747) (Обзор элементов управления веб-сервера RadioButton и RadioButtonList), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton> и <xref:System.Web.UI.WebControls.RadioButton>.

 ![Скрытый элемент HTML-страницы](../../ide/reference/media/vxhidden.gif "вксхидден") **ввода (скрытого)**

 Вставляет элемент `input` объекта `type="hidden"`. По умолчанию `id="Hidden1"` вставляется для первого скрытого поля, `id="Hidden2"` для второго и т. д.

 Когда вы перетаскиваете элемент **Ввод (скрытое поле)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:

```
<input id="Hidden1" type="hidden" name="Hidden1">
```

 Дополнительные сведения см. в статьях [HTML Input Controls](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de) (Элементы управления для ввода HTML), [Декларативный синтаксис серверного элемента управления HtmlInputHidden](https://msdn.microsoft.com/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9) и <xref:System.Web.UI.HtmlControls.HtmlInputHidden>.

 **Textarea** ![Текстовая область панели инструментов HtmlPage](../../ide/reference/media/vxtextarea.gif "вкстекстареа") в TextArea

 Вставляет элемент `textarea`. Можно изменить размер текстовой области или с помощью полос прокрутки просматривать текст, выходящий за пределы области отображения. Чтобы изменить отображаемый текст по умолчанию, измените атрибут `value`. По умолчанию `id="textarea1"` вставляется для первой текстовой области, `id=" textarea 2"` для второй и т. д.

 Когда вы перетаскиваете элемент **Текстовая область** на поверхность конструктора, в документ вставляется следующая HTML-разметка:

```
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

 Дополнительные сведения см. в разделе [декларативный синтаксис серверного элемента управления HtmlTextArea](https://msdn.microsoft.com/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), <xref:System.Web.UI.HtmlControls.HtmlTextArea> и <xref:System.Web.UI.WebControls.TextBox> .

> [!IMPORTANT]
> Рекомендуется проверить весь пользовательский ввод. Дополнительные сведения см. в разделе [Проверка пользовательского ввода на веб-страницах ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 **Table** ![Снимок экрана HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif "вкстабле") таблицы

 Вставляет элемент `table`.

 Когда вы перетаскиваете элемент **Таблица** на поверхность конструктора, в документ вставляется следующая HTML-разметка:

```
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

 Дополнительные сведения см. в статьях [Предыдущие версии продуктов, служб и технологий Майкрософт](https://msdn.microsoft.com/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [Table, TableRow, and TableCell Web Server Control Overview](https://msdn.microsoft.com/library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a) (Обзор элементов управления веб-сервера Table, TableRow и TableCell), <xref:System.Web.UI.HtmlControls.HtmlTable> и <xref:System.Web.UI.WebControls.Table>.

 **Image** ![Элемент изображения HTML-страницы](../../ide/reference/media/vximage.gif "вксимаже") изображения

 Вставляет элемент `img`. Измените этот элемент, чтобы указать его `src` и текст `alt`.

 Когда вы перетаскиваете элемент **Изображение** на поверхность конструктора, в документ вставляется следующая HTML-разметка:

```
<img alt="" src="">
```

 Дополнительные сведения см. в разделе [декларативный синтаксис серверного элемента управления HtmlImage](https://msdn.microsoft.com/528430e8-ced1-47d1-8db2-942e734a61f6), [Общие сведения об элементе управления Image Web Server](https://msdn.microsoft.com/library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9), <xref:System.Web.UI.HtmlControls.HtmlImage> , <xref:System.Web.UI.HtmlControls.HtmlInputImage> и <xref:System.Web.UI.WebControls.Image> .

 **Выбрать** ![раскрывающийся список панели элементов страницы HTML](../../ide/reference/media/vxdropdown.gif "вксдропдовн")

 Вставляет элемент `select` раскрывающегося списка (без атрибута `size`). По умолчанию `id="select1"` вставляется для первого списка, `id="select2"` для второго и т. д.

 Когда вы перетаскиваете элемент **Выбрать** на поверхность конструктора, в документ вставляется следующая HTML-разметка:

```
<select id="select1" name="select1"><option selected></option></select>
```

 Можно создать многострочный элемент `select`, увеличивая значение свойства размера.

 Дополнительные сведения см. в статьях [Декларативный синтаксис серверного элемента управления HtmlSelect](https://msdn.microsoft.com/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [How to: Create Scripts and Edit Event Handlers](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d) (Руководство по созданию скриптов и редактированию обработчиков событий), [DropDownList Web Server Control Overview](https://msdn.microsoft.com/library/517dd1a4-8df3-4c9f-8c89-1549a1aee608) (Обзор элемента управления веб-сервера DropDownList), [ListBox Web Server Control Overview](https://msdn.microsoft.com/library/c08ee025-787a-408d-858e-a4a5fdb61d97) (Обзор элемента управления веб-сервера ListBox), <xref:System.Web.UI.HtmlControls.HtmlSelect> и <xref:System.Web.UI.WebControls.DropDownList>.

 Элемент горизонтального ![правила HTML-страницы](../../ide/reference/media/vxhorizontal.gif "вксхоризонтал") **горизонтального правила**

 Вставляет элемент `hr`. Для увеличения толщины линии измените атрибут `size`.

 Когда вы перетаскиваете элемент **Горизонтальная линия** на поверхность конструктора, в документ вставляется следующая HTML-разметка:

```
<hr width="100%" size=1>
```

 Дополнительные сведения см. в разделе [Элемент управления горизонтальной линии HTML](https://msdn.microsoft.com/library/bf6df0a8-9844-404d-8a9a-3455b0180f2f).

 **Div** ![Метка HTML-страницы](../../ide/reference/media/vxlabel.gif "вкслабел") div

 Вставляет элемент `div`, включающий атрибут `ms_positioning="FlowLayout"`. За исключением ширины и высоты, этот элемент аналогичен панели потокового макета. Чтобы форматировать текст, содержащийся в элементе `div`, добавьте атрибут `class="stylename"` в открывающий тег.

 Когда вы перетаскиваете элемент **ДИВ** на поверхность конструктора, в документ вставляется следующая HTML-разметка:

```
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

 Дополнительные сведения см. в статьях [HTML Div Control](https://msdn.microsoft.com/library/585fa702-4408-4af1-a92b-68d77ee5e995) (HTML-элемент управления Div), [Label Web Server Control Overview](https://msdn.microsoft.com/library/990558d1-4b22-4f28-b100-78a434b3c5ac) (Обзор элемента управления веб-сервера Label) и <xref:System.Web.UI.WebControls.Label>.

## <a name="see-also"></a>См. также:
 [Панель элементов](../../ide/reference/toolbox.md) ["Стандартный",](https://msdn.microsoft.com/library/35e9320d-fcbd-474b-8b8f-55705e9a1870) [элементы управления HTML](https://msdn.microsoft.com/library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be) панели элементов
