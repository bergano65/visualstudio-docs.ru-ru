---
title: Просмотр прослушивателей событий DOM | Документация Майкрософт
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
- DOM events, viewing [Windows Store apps]
- event listeners, viewing [Windows Store apps]
ms.assetid: d5b679e7-87dd-4cec-9176-883db6ff0781
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ed3a4e4f67ef8a7cc1e13e513d2f03db5f755363
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "59003006"
---
# <a name="view-dom-event-listeners"></a>Просмотр прослушивателей событий DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Применяется к Windows и Windows Phone] (.. /Image/windows_and_phone_content.PNG «windows_and_phone_content»)

 **События** вкладке проводника DOM отображаются события, связанные с элементом DOM. Каждый узел верхнего уровня в **события** вкладка представляет событие, которое содержит активные подписчики. Узел верхнего уровня содержит вложенные узлы, представляющие зарегистрированные прослушиватели событий для указанного события. Помимо просмотра прослушивателей событий, этой вкладкой можно пользоваться для перехода к расположению прослушивателя событий в коде JavaScript. Информация, содержащаяся в данном разделе, относится к приложениям Магазина на базе HTML и JavaScript.

 В списке на **события** вкладке является динамическим. Если добавить прослушиватель событий во время выполнения приложения, в списке появится новый прослушиватель событий. Сведения о добавлении и удалении прослушивателей событий см. в разделе [советы по решению проблем с прослушивателями событий](#Tips) в этом разделе.

> [!NOTE]
>  Прослушиватели событий для элементов кода, которые не являются элементами DOM, таких как `xhr`, не отображаются на **события** вкладки.

## <a name="view-event-listeners-for-dom-elements"></a>Просмотр прослушивателей событий для элементов DOM
 В этом примере показано приложение Магазина Windows Phone. Описанные здесь возможности проводника DOM также поддерживаются для приложений Магазина Windows.

#### <a name="to-view-event-listeners"></a>Просмотр прослушивателей событий

1.  Создайте в Visual Studio приложение JavaScript, используя шаблон проекта "Приложение с Pivot" Windows Phone.

2.  Открыв шаблон в Visual Studio, выберите **Emulator 8.1 WVGA 4 in 512 МБ** в раскрывающемся списке на панели инструментов отладки в отладчике:

     ![Выбор цели отладки](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")

3.  Нажмите клавишу F5, чтобы запустить приложение в режиме отладки.

4.  В запущенном приложении, перейдите к **раздел 3** элементу pivot.

5.  Перейдите в Visual Studio (Alt+Tab или F12).

6.  В проводнике DOM выберите `Find` в правом верхнем углу.

7.  Введите команду `ListView`и нажмите клавишу ВВОД.

8.  При необходимости выберите **Далее** кнопку, чтобы найти `DIV` , представляющего `ListView` управления (этот элемент имеет `data-win-control` значение `WinJS.UI.ListView`).

     Теперь элемент `DIV` должен быть выбран в проводнике DOM.

9. Выберите **события** вкладку на панели в правой части проводника DOM.

     Теперь можно увидеть события с активными подписчиками для элемента `DIV`, как показано на ниже.

     ![Вкладке "события" проводника DOM](../debugger/media/js-dom-events.png "JS_DOM_Events")

10. Чтобы найти прослушиватели событий для этих событий, выберите связанные ссылки на файл JavaScript.

11. Чтобы быстро идентифицировать прослушиватели событий для родительских элементов в иерархии DOM, выберите родительский элемент в иерархическом списке в нижней части проводника DOM.

     ![Выбор родительских элементов в иерархии DOM](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")

     **События** вкладке отображаются прослушиватели событий для любого элемента, выбранного в иерархическом списке.

###  <a name="Tips"></a> Советы по решению проблем с прослушивателями событий
 В некоторых сценариях приложений прослушиватели событий необходимо явным образом удалить с помощью [removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx). Используйте **события** вкладку в проводнике DOM, чтобы проверить, были удалены прослушиватели событий из элементов DOM во время выполнения кода. Далее приведено несколько советов по устранению проблем такого типа:

-   Для приложений, которые используют модель одностраничной навигации, реализованы в Visual Studio [шаблоны проектов](http://msdn.microsoft.com/library/windows/apps/hh758331.aspx), обычно необязательно удалять прослушиватели событий для объектов, таких как элементы DOM, которые являются частью страницы. В данном сценарии элемент DOM и сопоставленные с ним прослушиватели событий имеют одинаковое время существования и могут участвовать в сборе мусора.

-   Если время существования элемента DOM или объекта отличается от времени существования сопоставленного прослушивателя событий, вам может потребоваться вызвать метод `removeEventListener`. Например, если вы используете событие `window.onresize`, может потребоваться удалить прослушиватель событий при покидании той страницы, на которой обрабатывается это событие.

-   Если `removeEventListener` не удается удалить указанный прослушиватель, он может быть вызван в другом экземпляре объекта. Можно использовать [метод bind (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) метод, чтобы устранить эту проблему, при добавлении прослушивателя.

-   Чтобы удалить прослушиватель событий, который был добавлен с помощью [метод bind (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) или используя анонимную функцию, сохраните экземпляр функции при добавлении прослушивателя. Ниже описан способ безопасного использования данного шаблона:

    ```javascript
    // You could use the following code within the constructor function of an object, or
    // in the ready function of a PageControl object (Store app).
    this.storedHandler = this._handlerFunc.bind(this);
    elem.addEventListener('mouseup', this.storedHandler);

    // In this example, add the following code in the PageControl object's unload function.
    elem.removeEventListener('mouseup', this.storedHandler);

    ```

     Если вы используете следующий код вместо сохранения ссылки на привязанную функцию, то не сможете удалить прослушиватель событий явным образом:

    ```javascript
    // Avoid this pattern. No reference to the bound function is available.
    elem.addEventListener('mouseup', this._handlerFunc.bind(this));
    ```

-   Вы не можете удалить прослушиватель событий с помощью `removeEventListener`, если добавили его с помощью атрибута `obj.on<eventname>`, такого как `window.onresize = handlerFunc`.

-   Использование анализатора памяти JavaScript для [память JavaScript](../profiling/javascript-memory.md) в вашем приложении. Прослушиватели событий, которые необходимо явным образом удалить, могут отображаться в качестве утечки памяти.

## <a name="see-also"></a>См. также

- [Краткое руководство. Отладка HTML и CSS](../debugger/quickstart-debug-html-and-css.md)
- [Отладка стилей CSS с использованием проводника DOM](../debugger/debug-css-styles-using-dom-explorer.md)
- [Отладка макета с использованием проводника DOM](../debugger/debug-layout-using-dom-explorer.md)