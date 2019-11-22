---
title: Debug layout using DOM Explorer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- box model [Windows Store apps], viewing
- debugging layout [Windows Store apps]
- layout, debugging [Windows Store apps]
ms.assetid: ded6566d-fc29-49a7-8029-dee8e50fe733
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5dd40381b8f5ba4807e95cfcf5e5b7d54afd77e2
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298394"
---
# <a name="debug-layout-using-dom-explorer"></a>Отладка макета с использованием проводника DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Applies to Windows and Windows Phone](../Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 На вкладке **Макет** проводника DOM отображается [рамочная модель CSS](https://go.microsoft.com/fwlink/?LinkID=238778) для выбранного элемента в приложении [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , приложении Магазина Windows Phone или приложении, созданном с помощью инструментов Visual Studio для Apache Cordova. С помощью визуального представления рамочной модели можно находить и изменять значения, связанные с макетом и влияющие на внешний вид элементов.  
  
> [!TIP]
> Изменения, вносимые на вкладке **Макет** , не являются постоянными. Вы можете внести постоянные изменения в исходный код, а затем обновить приложение, нажав кнопку **Обновить приложение Windows** (только для приложений Магазина Windows и Магазина Windows Phone) на панели инструментов «Отладка». Это позволит избежать перезапуска отладчика.  
  
 To use DOM Explorer to modify aspects of layout that aren’t shown in the box model, see [Quickstart: Debug HTML and CSS](../debugger/quickstart-debug-html-and-css.md) and [Debug CSS styles using DOM Explorer](../debugger/debug-css-styles-using-dom-explorer.md).  
  
## <a name="example-of-fixing-a-layout-issue"></a>Пример устранения проблемы с макетом  
 В этом примере показано, как выбрать элемент списка в шаблоне Hub/Pivot, интерпретировать значения рамочной модели на вкладке **Макет** , а затем изменить одно из значений свойств, чтобы устранить проблему с макетом.  
  
#### <a name="to-fix-the-layout-issue"></a>Устранение проблемы с макетом  
  
1. Создайте в Visual Studio новое приложение Магазина, использующее шаблон проекта Hub/Pivot.  
  
2. В общей папке pages\hub откройте файл hub.css.  
  
3. Замените представленный ниже код CSS.  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
    }  
    ```  
  
     следующим кодом CSS:  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
        margin-left: 5em;  
    }  
    ```  
  
4. В обозревателе решений выберите проект appName.WindowsPhone или appName.Windows и в контекстном меню выберите команду **Назначить запускаемым проектом** .  
  
5. В зависимости от запускаемого проекта выберите **Emulator 8.1 WVGA 512MB (RU)** или **Имитатор** в раскрывающемся списке на панели инструментов "Отладка" (значение по умолчанию —**Локальный компьютер** ).  
  
     ![Selecting a debug target](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
6. Нажмите клавишу F5, чтобы запустить приложение в режиме отладки.  
  
7. Откройте раздел 4 с помощью прокрутки или проведения.  
  
    > [!TIP]
    > Расположите эмулятор телефона или имитатор рядом с окном Visual Studio, чтобы можно было сразу же видеть результаты выбора и внесения изменений в стили CSS.  
  
     После загрузки раздела 4 вы увидите, что нижние изображения отображаются неправильно. Изображение каждого элемента разрезано напополам, причем левая половина не отображается.  
  
8. Переключитесь на Visual Studio и щелкните **Выбор элемента** в проводнике DOM (или нажмите CTRL+B). При этом изменится режим выбора, то есть элемент можно будет выбирать щелчком, и приложение появится на переднем плане. Вернуть предыдущий режим можно одним щелчком.  
  
    > [!TIP]
    > Кроме того, выбрать HTML-элементы можно непосредственно в проводнике DOM с помощью клавиш со стрелками или иных методов. For more info on selecting elements, see [Quickstart: Debug HTML and CSS](../debugger/quickstart-debug-html-and-css.md).  
  
9. В эмуляторе телефона или имитаторе выберите серую правую половину одного из изображений, разрезанных напополам. Вокруг выбранного элемента появляется рамка, как показано здесь в эмуляторе Windows Phone:  
  
     ![Selecting a DOM element](../debugger/media/js-css-layout-select.png "JS_CSS_Layout_Select")  
  
    > [!TIP]
    > Имитатор поддерживает наведение на элементы для отображения рамки вокруг элементов DOM перед выбором одного из них. В эмуляторе Windows Phone данная функция не поддерживается.  
  
     При выборе элемента DOM проводник DOM автоматически выбирает соответствующий элемент IMG в Visual Studio. Элемент, выбранный в проводнике DOM, выглядит следующим образом:  
  
    ```html  
    <img src="ms-appx://guid/images/gray.png>   
    </img>  
    ```  
  
10. Click the **Layout** tab. This tab shows the box model of the selected element, as shown here in the Windows Phone Emulator.  
  
     ![Layout tab of DOM Explorer](../debugger/media/js-css-layout.png "JS_CSS_Layout")  
  
     Это представление позволяет получить некоторые полезные сведения об элементе:  
  
    - Цвета соответствуют выделению рамками в имитаторе при наведении указателя мыши на элементами. The blue color represents the \<img> element dimensions. Бежевый цвет представляет значения полей.  
  
    - Для левого поля (margin-left) установлено значение, что говорит о возможной причине проблемы, поскольку черной является именно левая часть изображений.  
  
    - Поля, в которых отображаются значения, равные 0 пикселей (например, "Граница" и "Заполнение"), позволяют сделать вывод, что соответствующие свойства CSS, скорее всего, не заданы.  
  
11. Чтобы увидеть, как применяется правило margin-left, откройте вкладку **Вычисленные** и найдите правило margin-left. Можно видеть, что для этого правила задано значение 5em, но вычисленное значение равно 66,66 пикселей или 146,66 пикселей — в зависимости от целевого устройства.  
  
    > [!TIP]
    > The **Computed** tab shows that the margin-left rule is set in the `..hubpage .hub. section4 .sub-image-row img` CSS selector, found in hub.css. В этом демонстрационном приложении исправление требуется внести именно в этот файл.  
  
     Кроме того, можно использовать вкладку **Макет** для тестирования изменений значений макета.  
  
12. На вкладке **Макет** выберите значение **66,66** или **146,66**, которое отображается в поле **Поле** в левой части окна.  
  
13. Введите `0` и нажмите клавишу ВВОД. (Изменить значение также можно с помощью клавиш СТРЕЛКА ВВЕРХ и СТРЕЛКА ВНИЗ).  
  
14. Select the other \<img> elements in DOM Explorer and change their margin-left values to 0.  
  
15. Перейдите в эмулятор телефона или в имитатор. Обновленные значения margin-left применяются к изображениям раздела 4. Эти значения также обновляются на вкладке **Вычисленные** в правиле margin-left.  
  
## <a name="see-also"></a>См. также раздел  
 [Quickstart: Debug HTML and CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Debug CSS styles using DOM Explorer](../debugger/debug-css-styles-using-dom-explorer.md)   
 [Просмотр прослушивателей событий DOM](../debugger/view-dom-event-listeners.md)
