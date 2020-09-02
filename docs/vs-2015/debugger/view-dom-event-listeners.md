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
ms.openlocfilehash: 64d4892080aaf0cf04e4b208b1a0bdb7a7a4480d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693576"
---
# <a name="view-dom-event-listeners"></a>Просмотр прослушивателей событий DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Применяется к Windows и Windows Phone] (.. /Video windows_and_phone_content.png "windows_and_phone_content")

 На вкладке **события** проводника DOM отображаются события, связанные с элементом DOM. Каждый верхний узел на вкладке **события** представляет событие с активными подписчиками. Узел верхнего уровня содержит вложенные узлы, представляющие зарегистрированные прослушиватели событий для указанного события. Помимо просмотра прослушивателей событий, этой вкладкой можно пользоваться для перехода к расположению прослушивателя событий в коде JavaScript. Информация, содержащаяся в данном разделе, относится к приложениям Магазина на базе HTML и JavaScript.

 Список на вкладке **события** является динамическим. Если добавить прослушиватель событий во время выполнения приложения, в списке появится новый прослушиватель событий. Сведения о добавлении и удалении прослушивателей событий см. в разделе [Советы по устранению проблем с прослушивателями событий](#Tips) в этой статье.

> [!NOTE]
> Прослушиватели событий для элементов кода, не являющихся элементами DOM, например `xhr` , не отображаются на вкладке **события** .

## <a name="view-event-listeners-for-dom-elements"></a>Просмотр прослушивателей событий для элементов DOM
 В этом примере показано приложение Магазина Windows Phone. Описанные здесь возможности проводника DOM также поддерживаются для приложений Магазина Windows.

#### <a name="to-view-event-listeners"></a>Просмотр прослушивателей событий

1. Создайте в Visual Studio приложение JavaScript, используя шаблон проекта "Приложение с Pivot" Windows Phone.

2. Открыв шаблон в Visual Studio, выберите **emulator 8,1 WVGA 4IN 512 МБ** в раскрывающемся списке на панели инструментов отладки в отладчике:

     ![Выбор цели отладки](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")

3. Нажмите клавишу F5, чтобы запустить приложение в режиме отладки.

4. В работающем приложении перейдите к элементу сведения **раздела 3** .

5. Перейдите в Visual Studio (Alt+Tab или F12).

6. В проводнике DOM выберите `Find` в правом верхнем углу.

7. Введите команду `ListView`и нажмите клавишу ВВОД.

8. При необходимости нажмите кнопку **Далее** , чтобы найти `DIV` элемент, представляющий `ListView` элемент управления (этот элемент имеет `data-win-control` значение `WinJS.UI.ListView` ).

     Теперь элемент `DIV` должен быть выбран в проводнике DOM.

9. Перейдите на вкладку **события** в правой части проводника DOM.

     Теперь можно увидеть события с активными подписчиками для элемента `DIV`, как показано на ниже.

     ![Вкладка "События" проводника DOM](../debugger/media/js-dom-events.png "JS_DOM_Events")

10. Чтобы найти прослушиватели событий для этих событий, выберите связанные ссылки на файл JavaScript.

11. Чтобы быстро идентифицировать прослушиватели событий для родительских элементов в иерархии DOM, выберите родительский элемент в иерархическом списке в нижней части проводника DOM.

     ![Выбор родительских элементов в иерархии DOM](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")

     На вкладке **события** отображаются прослушиватели событий для любого элемента, выбранного в списке Иерархия.

### <a name="tips-for-resolving-issues-with-event-listeners"></a><a name="Tips"></a> Советы по устранению проблем с прослушивателями событий
 В некоторых сценариях приложений необходимо явно удалить прослушиватели событий с помощью [ремовивентлистенер](https://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx). Используйте вкладку **события** в проводнике DOM, чтобы проверить, были ли удалены прослушиватели событий из элементов DOM во время выполнения кода. Далее приведено несколько советов по устранению проблем такого типа:

- Для приложений, использующих модель навигации с одной страницей, реализованную в [шаблонах проектов](https://msdn.microsoft.com/library/windows/apps/hh758331.aspx)Visual Studio, обычно не требуется удалять прослушиватели событий, зарегистрированные для объектов, таких как элементы DOM, которые являются частью страницы. В данном сценарии элемент DOM и сопоставленные с ним прослушиватели событий имеют одинаковое время существования и могут участвовать в сборе мусора.

- Если время существования элемента DOM или объекта отличается от времени существования сопоставленного прослушивателя событий, вам может потребоваться вызвать метод `removeEventListener`. Например, если вы используете событие `window.onresize`, может потребоваться удалить прослушиватель событий при покидании той страницы, на которой обрабатывается это событие.

- Если `removeEventListener` не удается удалить указанный прослушиватель, он может быть вызван в другом экземпляре объекта. Чтобы устранить эту проблему при добавлении прослушивателя, можно использовать метод [BIND (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) .

- Чтобы удалить прослушиватель событий, добавленный с помощью [метода Bind (функция)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) или анонимной функции, сохраните экземпляр функции при добавлении прослушивателя. Ниже описан способ безопасного использования данного шаблона:

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

- Вы не можете удалить прослушиватель событий с помощью `removeEventListener`, если добавили его с помощью атрибута `obj.on<eventname>`, такого как `window.onresize = handlerFunc`.

- Используйте анализатор памяти JavaScript для [памяти JavaScript](../profiling/javascript-memory.md) в приложении. Прослушиватели событий, которые необходимо явным образом удалить, могут отображаться в качестве утечки памяти.

## <a name="see-also"></a>См. также:

- [Краткое руководство. Отладка HTML и CSS](../debugger/quickstart-debug-html-and-css.md)
- [Отладка стилей CSS с использованием проводника DOM](../debugger/debug-css-styles-using-dom-explorer.md)
- [Отладка макета с использованием проводника DOM](../debugger/debug-layout-using-dom-explorer.md)