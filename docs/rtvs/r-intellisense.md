---
title: IntelliSense для кода R
description: Visual Studio IntelliSense позволяет при вводе кода R просмотреть сведения о функциях и завершениях, а также элементы объекта и фрагменты кода.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: a9efdae5623c00abe4626d1bbb21af4a790fa487
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35666869"
---
# <a name="intellisense"></a>IntelliSense

IntelliSense в Visual Studio отображает сведения о функциях, которые можно вызывать, элементах объектов, аргументах функций и [фрагментах кода](code-snippets-for-r.md) прямо в представлении при написании кода. IntelliSense также отображает возможные варианты при вводе и автоматически завершает их при нажатии клавиш **TAB** или **ВВОД** (сведения о вкладке **Дополнительно** см. в разделе, посвященном [параметрам редактора](editing-r-code-in-visual-studio.md#editor-options)). IntelliSense доступен как в редакторе, так и в [интерактивном окне](interactive-repl-for-r-in-visual-studio.md).

![IntelliSense — отображение сигнатуры функции](media/intellisense-function-signature.png)

При вводе функции или другого оператора технология IntelliSense предлагает меню автозавершения ввода, содержимое которого отсортировано с учетом уже введенного текста (с учетом регистра).

![Меню автозавершения IntelliSense](media/intellisense-auto-complete-menu.png)

Нажмите клавишу **TAB** (или **ВВОД** или **ПРОБЕЛ**, в зависимости от заданных параметров), чтобы вставить элемент, выбранный в раскрывающемся списке. Выбор можно изменить с помощью клавиш со стрелками.

IntelliSense также предлагает варианты для членов объектов R.

![IntelliSense — предложения для членов объекта](media/intellisense-auto-complete-r-objects.png)

При нажатии клавиши **ESC** меню полностью закрывается. Чтобы снова открыть его, нажмите клавиши **CTRL**+**ПРОБЕЛ**.

При вводе открывающей `(` для вызова функции выполняется вставка закрывающей `)` и открывается справка по сигнатуре, как было указано выше.

![IntelliSense — отображение справки по сигнатуре для функции](media/intellisense-function-signature.png)

Чтобы закрыть всплывающее окно, нажмите клавишу **ESC**; чтобы открыть его снова для сигнатур функций, нажмите клавиши **CTRL**+**SHIFT**+**ПРОБЕЛ**.

> [!Tip]
> Если справка по параметру скрывает текст под ним, нажмите и удерживайте клавишу **CTRL**, чтобы сделать текст справки прозрачным.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>IntelliSense для определяемых пользователем функций и переменных

IntelliSense применяется для определяемых пользователем функций в том же файле, включая завершение имени параметра.

![IntelliSense для определяемых пользователем функций](media/intellisense-same-file-functions.png)

![IntelliSense — автозавершение параметра для определяемых пользователем функций](media/intellisense-parameter-completion.png)

IntelliSense также применяется для переменных в том же файле и в текущем сеансе.

![IntelliSense — автозавершение переменной](media/intellisense-variable-completion.png)

> [!Note]
> В интерактивном окне IntelliSense рассматривает только имена в текущем сеансе R и пропускает файлы в проекте.

## <a name="code-suggestions"></a>Предложения кода

Когда в поле появляется лампочка (называется смарт-тегом), Visual Studio сообщает, что имеется ярлык для часто используемого действия. Например, в редакторе наведите указатель мыши на строку с оператором `library`, чтобы отобразить лампочку. При выборе лампочки отображаются доступные параметры.

![Смарт-теги для R в редакторе](media/intellisense-smart-tags.png)
