---
title: "Вкладка \"HTML\", панель элементов | Документы Майкрософт"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eab9e96906e5d6bd31ef0f84bebf635c4c104b3d
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2018
---
# <a name="toolbox-html-tab"></a>Вкладка HTML, панель элементов
Вкладка **HTML** панели элементов предоставляет компоненты, которые полезны для использования на веб-страницах и веб-формах. Для просмотра этой вкладки сначала откройте HTML-документ в конструкторе HTML. В меню **Вид** щелкните **Панель элементов** и откройте вкладку **HTML** на панели элементов.  

 Для создания экземпляра средства на вкладке **HTML** дважды щелкните средство, чтобы добавить его в документ в текущем положении курсора, или выберите средство и перетащите его в нужное место на поверхности редактирования.  

## <a name="tasks"></a>Задачи  

-   [Использование панели элементов](../../ide/using-the-toolbox.md)  

## <a name="ui-elements"></a>Элементы пользовательского интерфейса  
 По умолчанию на вкладке HTML доступны указанные ниже средства.  

 **Указатель**  
 ![Указатель HTMLpage конструктора ASP.NET для мобильных устройств](../../ide/reference/media/vxpointer.gif "vxPointer")  

 Это средство выбирается по умолчанию при открытии любой вкладки области элементов. Его нельзя удалить. Указатель позволяет перетаскивать объекты на поверхность конструктора, изменять их размеры и перемещать по странице или форме. Дополнительные сведения см. в разделе [Использование панели элементов](../../ide/using-the-toolbox.md).  

 **Ввод (кнопка)**  
 ![Кнопка веб-страницы HTML](../../ide/reference/media/vxbutton.gif "vxButton")  

 Вставляет элемент `input` объекта `type="button"`. Чтобы изменить отображаемый текст, измените свойство `name`. По умолчанию `id="Button1"` вставляется для первой кнопки, `id="Button2"` для второй и т. д.  

 Когда вы перетаскиваете элемент **Ввод (кнопка)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  

```  
<input id="Button1" type="button" value="Button" name="Button1">  
```  

 **Ввод (кнопка сброса)**  
 ![Снимок экрана HTMLpageResetButton](../../ide/reference/media/vxreset.gif "vxReset")  

 Вставляет элемент `input` объекта `type="reset"`. Чтобы изменить отображаемый текст, измените свойство `name`. По умолчанию `id="Reset1"` вставляется для первой кнопки сброса, `id="Reset2"` для второй и т. д.  

 Когда вы перетаскиваете элемент **Ввод (кнопка сброса)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  

```  
<input id="Reset1" type="reset" value="Reset" name="Reset1">  
```  

 **Ввод (кнопка отправки)**  
 ![Снимок экрана HTMLpageToolbarSubmitButton](../../ide/reference/media/vxsubmit.gif "vxSubmit")  

 Вставляет элемент `input` объекта `type="submit"`. Чтобы изменить отображаемый текст, измените свойство `name`. По умолчанию `id="Submit1"` вставляется для первой кнопки отправки, `id="Submit2"` для второй и т. д.  

 Когда вы перетаскиваете элемент **Ввод (кнопка отправки)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  

```  
<input id="Submit1" type="submit" value="Submit" name="Submit1">  
```  

 **Ввод (текст)**  
 ![Снимок экрана HTMLpageToolbarTextField](../../ide/reference/media/vxtextfield.gif "vxTextfield")  

 Вставляет элемент `input` объекта `type="text"` в документ. Чтобы изменить отображаемый текст по умолчанию, измените атрибут `value`. По умолчанию `id="Text1"` вставляется для первого текстового поля, `id="Text2"` для второго и т. д.  

 Когда вы перетаскиваете элемент **Ввод (текст)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  

```  
<input id="Text1" TYPE="text" value="Text Field" name="Text1">  
```  

> [!IMPORTANT]
>  Рекомендуется проверить весь пользовательский ввод. Дополнительные сведения см. в статье [Validating User Input in ASP.NET Web Pages (Razor) Sites](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).  

 **Ввод (файл)**  
 ![Поле файла страницы HTML](../../ide/reference/media/vxfilefield.gif "vxFilefield")  

 Вставляет элемент `input` объекта `type="file"` в документ. По умолчанию `id="File1"` вставляется для первого поля файла, `id="File2"` для второго и т. д.  

 Когда вы перетаскиваете элемент **Ввод (файл)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  

```  
<input id="File1" type="file" name="File1">  
```  

> [!IMPORTANT]
>  Рекомендуется проверить весь пользовательский ввод. Дополнительные сведения см. в статье [Validating User Input in ASP.NET Web Pages (Razor) Sites](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).  

 **Ввод (пароль)**  
 ![Поле пароля Visual Studio](../../ide/reference/media/vxpassword.gif "vxPassword")  

 Вставляет элемент `input` объекта `type="password"`. По умолчанию `id="Password1"` вставляется для первого поля пароля, `id="Password2"` для второго и т. д.  

 Когда вы перетаскиваете элемент **Ввод (пароль)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  

```  
<input id="Password1" type="password" name="Password1">  
```  

> [!IMPORTANT]
>  Если приложение передает имена пользователей и пароли, следует настроить веб-сайт, чтобы использовать SSL для шифрования передачи. Подробнее см. в подразделе "Обеспечение безопасности подключений с помощью SSL" раздела [Руководство по операциям IIS](http://go.microsoft.com/fwlink/?linkid=47856). Дополнительно рекомендуется проверить весь пользовательский ввод. Дополнительные сведения см. в статье [Validating User Input in ASP.NET Web Pages (Razor) Sites](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).  

 **Ввод (флажок)**  
 ![Параметр Checkbox панели элементов веб-страницы HTML](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")  

 Вставляет элемент `input` объекта `type="checkbox"`. Чтобы изменить отображаемый текст, измените свойство `name`. По умолчанию `id="Checkbox1"` вставляется для первого флажка, `id="Checkbox2"` для второго и т. д.  

 Когда вы перетаскиваете элемент **Ввод (флажок)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  

```  
<input id="Checkbox1" type="checkbox" name="Checkbox1">   
```  

 **Ввод (переключатель)**  
 ![Снимок экрана VisualStudioHTMLpageRadioButton](../../ide/reference/media/vxradio.gif "vxRadio")  

 Вставляет элемент `input` объекта `type="radio"`. Чтобы изменить отображаемый текст, измените свойство `name`. По умолчанию `id="Radio1"` вставляется для первого переключателя, `id="Radio2"` для второго и т. д.  

 Когда вы перетаскиваете элемент **Ввод (переключатель)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  

```  
<input id="Radio1" type="radio" name="Radio1">  
```  

 **Ввод (скрытое поле)**  
 ![Скрытый элемент страницы HTML](../../ide/reference/media/vxhidden.gif "vxhidden")  

 Вставляет элемент `input` объекта `type="hidden"`. По умолчанию `id="Hidden1"` вставляется для первого скрытого поля, `id="Hidden2"` для второго и т. д.  

 Когда вы перетаскиваете элемент **Ввод (скрытое поле)** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  

```  
<input id="Hidden1" type="hidden" name="Hidden1">   
```  

 **Текстовая область**  
 ![Область текста панели инструментов HTMLpage](../../ide/reference/media/vxtextarea.gif "vxTextarea")  

 Вставляет элемент `textarea`. Можно изменить размер текстовой области или с помощью полос прокрутки просматривать текст, выходящий за пределы области отображения. Чтобы изменить отображаемый текст по умолчанию, измените атрибут `value`. По умолчанию `id="textarea1"` вставляется для первой текстовой области, `id=" textarea 2"` для второй и т. д.  

 Когда вы перетаскиваете элемент **Текстовая область** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  

```  
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>   
```  

> [!IMPORTANT]
>  Рекомендуется проверить весь пользовательский ввод. Дополнительные сведения см. в статье [Validating User Input in ASP.NET Web Pages (Razor) Sites](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).  

 **Таблица**  
 ![Снимок экрана HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif "vxTable")  

 Вставляет элемент `table`.  

 Когда вы перетаскиваете элемент **Таблица** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  

```  
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>   
```  

**Изображение**  
 ![Элемент изображения страницы HTML](../../ide/reference/media/vximage.gif "vxImage")  

 Вставляет элемент `img`. Измените этот элемент, чтобы указать его `src` и текст `alt`.  

 Когда вы перетаскиваете элемент **Изображение** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  

```  
<img alt="" src="">  
```  

 **Выбрать**  
 ![Открывающаяся панель элементов страницы HTML](../../ide/reference/media/vxdropdown.gif "vxDropdown")  

 Вставляет элемент `select` раскрывающегося списка (без атрибута `size`). По умолчанию `id="select1"` вставляется для первого списка, `id="select2"` для второго и т. д.  

 Когда вы перетаскиваете элемент **Выбрать** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  

```  
<select id="select1" name="select1"><option selected></option></select>  
```  

 Можно создать многострочный элемент `select`, увеличивая значение свойства размера.  

 **Горизонтальная линия**  
 ![Элемент горизонтальной линии страницы HTML](../../ide/reference/media/vxhorizontal.gif "vxHorizontal")  

 Вставляет элемент `hr`. Для увеличения толщины линии измените атрибут `size`.  

 Когда вы перетаскиваете элемент **Горизонтальная линия** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  

```  
<hr width="100%" size=1>   
```  

 **ДИВ**  
 ![Метка страницы HTML](../../ide/reference/media/vxlabel.gif "vxLabel")  

 Вставляет элемент `div`, включающий атрибут `ms_positioning="FlowLayout"`. За исключением ширины и высоты, этот элемент аналогичен панели потокового макета. Чтобы форматировать текст, содержащийся в элементе `div`, добавьте атрибут `class="stylename"` в открывающий тег.  

 Когда вы перетаскиваете элемент **ДИВ** на поверхность конструктора, в документ вставляется следующая HTML-разметка:  

```  
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>  
```  

## <a name="see-also"></a>См. также  
 [Панель элементов](../../ide/reference/toolbox.md)   
 [Использование панели элементов](../../ide/using-the-toolbox.md)   
