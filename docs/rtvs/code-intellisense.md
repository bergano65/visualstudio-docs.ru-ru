---
title: "IntelliSense для кода R в Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3677-e5ec-4e11-82a8-d914a93b1aa9
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 359b9dc6bae84bb6d89e5f0f646c0b8fed5898ec
ms.contentlocale: ru-ru
ms.lasthandoff: 05/12/2017

---


# <a name="intellisense"></a>IntelliSense

IntelliSense в Visual Studio отображает сведения о функции, которую можно вызывать, члены объектов, аргументы функции и [фрагменты кода](code-snippets.md) прямо в текущей строке при написании кода. IntelliSense также отображает возможные варианты при вводе и автоматически завершает их при нажатии клавиш TAB или ВВОД (сведения о вкладке **Дополнительно** см. в разделе, посвященном [параметрам редактора](code-editing.md#editor-options)). IntelliSense доступен как в редакторе, так и в [интерактивном окне](interactive-repl.md).

![IntelliSense — отображение сигнатуры функции](media/intellisense-function-signature.png) 

При вводе функции или другого оператора технология IntelliSense предлагает меню автозавершения ввода, содержимое которого отсортировано с учетом уже введенного текста (с учетом регистра).

![Меню автозавершения IntelliSense](media/intellisense-auto-complete-menu.png)

Нажмите клавишу TAB (или ВВОД или ПРОБЕЛ, в зависимости от заданных параметров), чтобы вставить элемент, выбранный в раскрывающемся списке. Выбор можно изменить с помощью клавиш со стрелками. 

IntelliSense также предлагает варианты для членов объектов R.
 
![IntelliSense — предложения для членов объекта](media/intellisense-auto-complete-r-objects.png)
 
При нажатии клавиши ESC меню полностью закрывается. Чтобы снова открыть его , нажмите клавиши CTRL + ПРОБЕЛ.

При вводе открывающей `(` для вызова функции выполняется вставка закрывающей `)` и открывается справка по сигнатуре, как было указано выше.

![IntelliSense — отображение справки по сигнатуре для функции](media/intellisense-function-signature.png)

Чтобы закрыть всплывающее окно, нажмите клавишу ESC; чтобы открыть его снова, нажмите клавиши CTRL + SHIFT + ПРОБЕЛ.

> [!Tip]
> Если справка по параметру скрывает текст под ним, например в редакторе файлов, нажмите и удерживайте клавишу CTRL, чтобы сделать текст справки по параметру прозрачным.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>IntelliSense для определяемых пользователем функций и переменных

IntelliSense применяется для определяемых пользователем функций в том же файле, включая завершение имени параметра.

![IntelliSense для определяемых пользователем функций](media/intellisense-same-file-functions.png)

![IntelliSense — автозавершение параметра для определяемых пользователем функций](media/intellisense-parameter-completion.png)

IntelliSense также применяется для переменных в том же файле и в текущем сеансе.

![IntelliSense — автозавершение переменной](media/intellisense-variable-completion.png)

> [!Note]
> В интерактивном окне IntelliSense рассматривает только имена в текущем сеансе R и пропускает файлы в проекте.

## <a name="code-suggestions"></a>Предложения кода

Когда в поле появляется лампочка (называется смарт-тегом), Visual Studio сообщает, что имеется ярлык для часто используемого действия. Например, в редакторе наведите указатель мыши на строку с оператором `library`, после чего в поле слева отобразится лампочка. При выборе лампочки отображаются доступные параметры.

![Смарт-теги для R в редакторе](media/intellisense-smart-tags.png)

