---
title: "Вкладка &quot;HTML&quot;, панель элементов | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: b1efeec49da120d438ac14d89c2f5e40321326ab
ms.lasthandoff: 02/22/2017

---
# <a name="toolbox-html-tab"></a>Вкладка HTML, панель элементов
Вкладка **HTML** панели элементов предоставляет компоненты, которые полезны для использования на веб-страницах и веб-формах. Для просмотра этой вкладки сначала откройте HTML-документ в конструкторе HTML. В меню **Вид** щелкните **Панель элементов** и откройте вкладку **HTML** на панели элементов.  
  
 Для создания экземпляра средства на вкладке **HTML** дважды щелкните средство, чтобы добавить его в документ в текущем положении курсора, или выберите средство и перетащите его в нужное место на поверхности редактирования.  
  
## <a name="tasks"></a>Задачи  
  
-   [Практическое руководство. Управление окном панели элементов](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
  
-   [Практическое руководство. Управление вкладками панели элементов](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db)  
  
## <a name="ui-elements"></a>Элементы пользовательского интерфейса  
 По умолчанию на вкладке HTML доступны указанные ниже средства.  
  
 **Указатель**  
 ![Указатель HTMLpage конструктора мобильных устройств ASP.NET](../../ide/reference/media/vxpointer.gif "vxPointer")  
  
 Это средство выбирается по умолчанию при открытии любой вкладки области элементов. Его нельзя удалить. Указатель позволяет перетаскивать объекты на поверхность конструктора, изменять их размеры и перемещать по странице или форме. Дополнительные сведения см. в разделах [Практическое руководство. Управление окном панели элементов](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2) и [Практическое руководство. Управление вкладками панели элементов](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 **Ввод (кнопка)**  
 ![Кнопка веб-страницы HTML](../../ide/reference/media/vxbutton.gif "vxButton")  
  
 Вставляет элемент `input` объекта `type="button"`. Чтобы изменить отображаемый текст, измените свойство `name`. По умолчанию `id="Button1"` вставляется для первой кнопки, `id="Button2"` для второй и т. д.  
  
 Когда вы перетаскиваете элемент **Ввод (кнопка)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  
  
```  
<input id="Button1" type="button" value="Button" name="Button1">  
```  
  
 Дополнительные сведения см. в разделах [Элементы управления ввода HTML](http://msdn.microsoft.com/Library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Декларативный синтаксис серверного элемента управления HtmlInputButton](http://msdn.microsoft.com/en-us/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [Практическое руководство. Создание скриптов и изменение обработчиков событий](http://msdn.microsoft.com/en-us/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Карта содержимого для серверных веб-элементов управления Button](http://msdn.microsoft.com/Library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton> и <xref:System.Web.UI.WebControls.Button>.  
  
 **Ввод (кнопка сброса)**  
 ![Снимок экрана HTMLpageResetButton](../../ide/reference/media/vxreset.gif "vxReset")  
  
 Вставляет элемент `input` объекта `type="reset"`. Чтобы изменить отображаемый текст, измените свойство `name`. По умолчанию `id="Reset1"` вставляется для первой кнопки сброса, `id="Reset2"` для второй и т. д.  
  
 Когда вы перетаскиваете элемент **Ввод (кнопка сброса)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  
  
```  
<input id="Reset1" type="reset" value="Reset" name="Reset1">  
```  
  
 Дополнительные сведения см. в разделах [Элементы управления ввода HTML](http://msdn.microsoft.com/Library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Декларативный синтаксис серверного элемента управления HtmlInputReset](http://msdn.microsoft.com/en-us/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton> и <xref:System.Web.UI.WebControls.Button>.  
  
 **Ввод (кнопка отправки)**  
 ![Снимок экрана HTMLpageToolbarSubmitButton](../../ide/reference/media/vxsubmit.gif "vxSubmit")  
  
 Вставляет элемент `input` объекта `type="submit"`. Чтобы изменить отображаемый текст, измените свойство `name`. По умолчанию `id="Submit1"` вставляется для первой кнопки отправки, `id="Submit2"` для второй и т. д.  
  
 Когда вы перетаскиваете элемент **Ввод (кнопка отправки)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  
  
```  
<input id="Submit1" type="submit" value="Submit" name="Submit1">  
```  
  
 Дополнительные сведения см. в разделах [Элементы управления ввода HTML](http://msdn.microsoft.com/Library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Декларативный синтаксис серверного элемента управления HtmlInputSubmit](http://msdn.microsoft.com/en-us/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton> и <xref:System.Web.UI.WebControls.Button>.  
  
 **Ввод (текст)**  
 ![Снимок экрана HTMLpageToolbarTextField](../../ide/reference/media/vxtextfield.gif "vxTextfield")  
  
 Вставляет элемент `input` объекта `type="text"` в документ. Чтобы изменить отображаемый текст по умолчанию, измените атрибут `value`. По умолчанию `id="Text1"` вставляется для первого текстового поля, `id="Text2"` для второго и т. д.  
  
 Когда вы перетаскиваете элемент **Ввод (текст)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  
  
```  
<input id="Text1" TYPE="text" value="Text Field" name="Text1">  
```  
  
 Дополнительные сведения см. в разделах [Элементы управления ввода HTML](http://msdn.microsoft.com/Library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Декларативный синтаксис серверного элемента управления HtmlInputText](http://msdn.microsoft.com/en-us/87060d90-a11c-434d-9fc9-b03a8487041e), [Общие сведения о серверном веб-элементе управления TextBox](http://msdn.microsoft.com/Library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f), <xref:System.Web.UI.HtmlControls.HtmlInputText> и <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Рекомендуется проверить весь пользовательский ввод. Дополнительные сведения см. в разделе [Проверка пользовательского ввода на веб-страницах ASP.NET](http://msdn.microsoft.com/Library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Ввод (файл)**  
 ![Поле файла страницы HTML](../../ide/reference/media/vxfilefield.gif "vxFilefield")  
  
 Вставляет элемент `input` объекта `type="file"` в документ. По умолчанию `id="File1"` вставляется для первого поля файла, `id="File2"` для второго и т. д.  
  
 Когда вы перетаскиваете элемент **Ввод (файл)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  
  
```  
<input id="File1" type="file" name="File1">  
```  
  
 Дополнительные сведения см. в разделах [Элементы управления ввода HTML](http://msdn.microsoft.com/Library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Декларативный синтаксис серверного элемента управления HtmlInputFile](http://msdn.microsoft.com/en-us/a817b4a0-056f-4c17-a696-b9fdcde43db6) и <xref:System.Web.UI.HtmlControls.HtmlInputFile>.  
  
> [!IMPORTANT]
>  Рекомендуется проверить весь пользовательский ввод. Дополнительные сведения см. в разделе [Проверка пользовательского ввода на веб-страницах ASP.NET](http://msdn.microsoft.com/Library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Ввод (пароль)**  
 ![Поле пароля Visual Studio](../../ide/reference/media/vxpassword.gif "vxPassword")  
  
 Вставляет элемент `input` объекта `type="password"`. По умолчанию `id="Password1"` вставляется для первого поля пароля, `id="Password2"` для второго и т. д.  
  
 Когда вы перетаскиваете элемент **Ввод (пароль)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  
  
```  
<input id="Password1" type="password" name="Password1">  
```  
  
 Дополнительные сведения см. в разделе [Элементы управления ввода HTML](http://msdn.microsoft.com/Library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Декларативный синтаксис серверного элемента управления HtmlInputPassword](http://msdn.microsoft.com/en-us/df703dd0-1624-4e5a-a547-c97f2f331b9f), [Практическое руководство. Установка серверного веб-элемента управления для ввода пароля](http://msdn.microsoft.com/Library/5b5069f3-64a1-435a-aee6-da263f4e6310) и [Практическое руководство. Проверка пользовательского ввода на странице веб-форм](http://msdn.microsoft.com/Library/7141d6ba-34f3-410b-b5cd-2102a24cb436).  
  
> [!IMPORTANT]
>  Если приложение передает имена пользователей и пароли, следует настроить веб-сайт, чтобы использовать SSL для шифрования передачи. Подробнее см. в подразделе "Обеспечение безопасности подключений с помощью SSL" раздела [Руководство по операциям IIS](http://go.microsoft.com/fwlink/?linkid=47856). Дополнительно рекомендуется проверить весь пользовательский ввод. Дополнительные сведения см. в разделе [Проверка пользовательского ввода на веб-страницах ASP.NET](http://msdn.microsoft.com/Library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Ввод (флажок)**  
 ![Параметр Checkbox панели элементов веб-страницы HTML](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")  
  
 Вставляет элемент `input` объекта `type="checkbox"`. Чтобы изменить отображаемый текст, измените свойство `name`. По умолчанию `id="Checkbox1"` вставляется для первого флажка, `id="Checkbox2"` для второго и т. д.  
  
 Когда вы перетаскиваете элемент **Ввод (флажок)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  
  
```  
<input id="Checkbox1" type="checkbox" name="Checkbox1">   
```  
  
 Дополнительные сведения см. в разделах [Элементы управления ввода HTML](http://msdn.microsoft.com/Library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Декларативный синтаксис серверного элемента управления HtmlInputCheckBox](http://msdn.microsoft.com/en-us/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [Общие сведения о серверных веб-элементах управления CheckBox и CheckBoxList](http://msdn.microsoft.com/Library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox> и <xref:System.Web.UI.WebControls.CheckBox>.  
  
 **Ввод (переключатель)**  
 ![Снимок экрана VisualStudioHTMLpageRadioButton](../../ide/reference/media/vxradio.gif "vxRadio")  
  
 Вставляет элемент `input` объекта `type="radio"`. Чтобы изменить отображаемый текст, измените свойство `name`. По умолчанию `id="Radio1"` вставляется для первого переключателя, `id="Radio2"` для второго и т. д.  
  
 Когда вы перетаскиваете элемент **Ввод (переключатель)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  
  
```  
<input id="Radio1" type="radio" name="Radio1">  
```  
  
 Дополнительные сведения см. в разделах [Элементы управления ввода HTML](http://msdn.microsoft.com/Library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Декларативный синтаксис серверного элемента управления HtmlInputRadioButton](http://msdn.microsoft.com/en-us/6e60ff63-cc57-46ef-bf96-e829e204ba33), [Общие сведения о серверных веб-элементах управления RadioButton и RadioButtonList](http://msdn.microsoft.com/Library/20eb383c-4b59-432b-bba3-e9d785107747), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton> и <xref:System.Web.UI.WebControls.RadioButton>.  
  
 **Ввод (скрытое поле)**  
 ![Скрытый элемент страницы HTML](../../ide/reference/media/vxhidden.gif "vxhidden")  
  
 Вставляет элемент `input` объекта `type="hidden"`. По умолчанию `id="Hidden1"` вставляется для первого скрытого поля, `id="Hidden2"` для второго и т. д.  
  
 Когда вы перетаскиваете элемент **Ввод (скрытое поле)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  
  
```  
<input id="Hidden1" type="hidden" name="Hidden1">   
```  
  
 Дополнительные сведения см. в разделах [Элементы управления ввода HTML](http://msdn.microsoft.com/Library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Декларативный синтаксис серверного элемента управления HtmlInputHidden](http://msdn.microsoft.com/en-us/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9) и <xref:System.Web.UI.HtmlControls.HtmlInputHidden>.  
  
 **Текстовая область**  
 ![Область текста панели инструментов HTMLpage](../../ide/reference/media/vxtextarea.gif "vxTextarea")  
  
 Вставляет элемент `textarea`. Можно изменить размер текстовой области или с помощью полос прокрутки просматривать текст, выходящий за пределы области отображения. Чтобы изменить отображаемый текст по умолчанию, измените атрибут `value`. По умолчанию `id="textarea1"` вставляется для первой текстовой области, `id=" textarea 2"` для второй и т. д.  
  
 Когда вы перетаскиваете элемент **Текстовая область** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  
  
```  
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>   
```  
  
 Дополнительные сведения см. в разделах [Декларативный синтаксис серверного элемента управления HtmlTextArea](http://msdn.microsoft.com/en-us/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), <xref:System.Web.UI.HtmlControls.HtmlTextArea> и <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Рекомендуется проверить весь пользовательский ввод. Дополнительные сведения см. в разделе [Проверка пользовательского ввода на веб-страницах ASP.NET](http://msdn.microsoft.com/Library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Таблица**  
 ![Снимок экрана HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif "vxTable")  
  
 Вставляет элемент `table`.  
  
 Когда вы перетаскиваете элемент **Таблица** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  
  
```  
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>   
```  
  
 Дополнительные сведения см. в разделах [Декларативный синтаксис серверного элемента управления HtmlTable](http://msdn.microsoft.com/en-us/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [Общие сведения о серверных веб-элементах управления Table, TableRow и TableCell](http://msdn.microsoft.com/Library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a), <xref:System.Web.UI.HtmlControls.HtmlTable> и <xref:System.Web.UI.WebControls.Table>.  
  
 **Изображение**  
 ![Элемент изображения страницы HTML](../../ide/reference/media/vximage.gif "vxImage")  
  
 Вставляет элемент `img`. Измените этот элемент, чтобы указать его `src` и текст `alt`.  
  
 Когда вы перетаскиваете элемент **Изображение** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  
  
```  
<img alt="" src="">  
```  
  
 Дополнительные сведения см. в разделах [Декларативный синтаксис серверного элемента управления HtmlImage](http://msdn.microsoft.com/en-us/528430e8-ced1-47d1-8db2-942e734a61f6), [Общие сведения о серверном веб-элементе управления Image](http://msdn.microsoft.com/Library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9), <xref:System.Web.UI.HtmlControls.HtmlImage>, <xref:System.Web.UI.HtmlControls.HtmlInputImage> и <xref:System.Web.UI.WebControls.Image>.  
  
 **Выбрать**  
 ![Открывающаяся панель элементов страницы HTML](../../ide/reference/media/vxdropdown.gif "vxDropdown")  
  
 Вставляет элемент `select` раскрывающегося списка (без атрибута `size`). По умолчанию `id="select1"` вставляется для первого списка, `id="select2"` для второго и т. д.  
  
 Когда вы перетаскиваете элемент **Выбрать** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  
  
```  
<select id="select1" name="select1"><option selected></option></select>  
```  
  
 Можно создать многострочный элемент `select`, увеличивая значение свойства размера.  
  
 Дополнительные сведения см. в разделах [Декларативный синтаксис серверного элемента управления HtmlSelect](http://msdn.microsoft.com/en-us/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [Практическое руководство. Создание скриптов и изменение обработчиков событий](http://msdn.microsoft.com/en-us/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Общие сведения о серверном веб-элементе управления DropDownList](http://msdn.microsoft.com/Library/517dd1a4-8df3-4c9f-8c89-1549a1aee608), [Общие сведения о серверном веб-элементе управления ListBox](http://msdn.microsoft.com/Library/c08ee025-787a-408d-858e-a4a5fdb61d97), <xref:System.Web.UI.HtmlControls.HtmlSelect> и <xref:System.Web.UI.WebControls.DropDownList>.  
  
 **Горизонтальная линия**  
 ![Элемент горизонтальной линии страницы HTML](../../ide/reference/media/vxhorizontal.gif "vxHorizontal")  
  
 Вставляет элемент `hr`. Для увеличения толщины линии измените атрибут `size`.  
  
 Когда вы перетаскиваете элемент **Горизонтальная линия** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  
  
```  
<hr width="100%" size=1>   
```  
  
 Дополнительные сведения см. в разделе [Элемент управления горизонтальной линии HTML](http://msdn.microsoft.com/Library/bf6df0a8-9844-404d-8a9a-3455b0180f2f).  
  
 **ДИВ**  
 ![Метка страницы HTML](../../ide/reference/media/vxlabel.gif "vxLabel")  
  
 Вставляет элемент `div`, включающий атрибут `ms_positioning="FlowLayout"`. За исключением ширины и высоты, этот элемент аналогичен панели потокового макета. Чтобы форматировать текст, содержащийся в элементе `div`, добавьте атрибут `class="stylename"` в открывающий тег.  
  
 Когда вы перетаскиваете элемент **ДИВ** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  
  
```  
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>  
```  
  
 Дополнительные сведения см. в разделах [Элемент управления HTML Div](http://msdn.microsoft.com/Library/585fa702-4408-4af1-a92b-68d77ee5e995), [Серверный веб-элемент управления Label](http://msdn.microsoft.com/Library/990558d1-4b22-4f28-b100-78a434b3c5ac) и <xref:System.Web.UI.WebControls.Label>.  
  
## <a name="see-also"></a>См. также  
 [Панель элементов](../../ide/reference/toolbox.md)   
 [Вкладка "Стандартные", панель элементов](http://msdn.microsoft.com/Library/35e9320d-fcbd-474b-8b8f-55705e9a1870)   
 [Элементы управления HTML](http://msdn.microsoft.com/Library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be)
