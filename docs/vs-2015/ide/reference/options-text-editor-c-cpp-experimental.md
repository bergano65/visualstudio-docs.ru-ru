---
title: "\"Параметры\", \"Текстовый редактор\", C/C++, \"Экспериментальный\" | Документация Майкрософт"
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5979363f16f2e9d78a2f50ffbb6511d03146caaa
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297857"
---
# <a name="options-text-editor-cc-experimental"></a>"Параметры", "Текстовый редактор", C/C++, "Экспериментальный"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Изменяя эти параметры, можно настроить поведение, связанное с IntelliSense и базой данных просмотра, при программировании на языке C или C++.

 Чтобы открыть эту страницу, в диалоговом окне **Параметры** в левой области разверните **Текстовый редактор**, разверните **C/C++** и щелкните **Экспериментальный**.

 Эти функции доступны в версии-кандидате Visual Studio 2015 с обновлением 1.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. См. раздел [Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="browsingnavigation"></a>Обзор и навигация
 **Enable New Database Engine** This should automatically speed up database population and make all database operations faster (with no loss in accuracy) for operations such as **Go To Definition** and **Find All References**. (Чтобы применить изменения, просто закройте и повторно откройте решение. Перезапускать Visual Studio не нужно.)

## <a name="intellisense"></a>IntelliSense
 **Member List Dot-To-Arrow** Replaces '.' with '->' when applicable for Member List.

## <a name="refactoring"></a>Рефакторинг
 **Enable Extract Function** Extract selected code to its own function and replace code with a call to the new function. Чтобы получить доступ к этой возможности, щелкните выделенный код правой кнопкой мыши и выберите пункт **Быстрые действия**или просто нажмите клавиши CTRL+точка [CTRL+.].

 **Enable Change Signature** Add, reorder, and delete parameters of a function and propagate the changes to all call sites. Чтобы получить доступ к этой возможности, щелкните правой кнопкой мыши в любом месте, где используется функция, и выберите пункт **Быстрые действия**или просто нажмите клавиши CTRL+точка [CTRL+.].

## <a name="text-editor"></a>Текстовый редактор
 **Enable Expand Scopes** If enabled, you can surround selected text with curly braces by typing '{' into the text editor.

 **Enable Expand Precedence** If enabled, you can surround selected text with parentheses by typing '(' into the text editor.

 Список дополнительных функций текстового редактора в галерее Visual Studio можно найти [здесь](https://go.microsoft.com/fwlink/?LinkId=692016). Примером может служить расширение [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), которое поддерживает перечисленные ниже возможности.

- **Добавление недостающих операторов #include** — для неизвестных символов в коде предлагаются подходящие операторы #include.

- **Добавление пространства имен using и полное определение символа** — аналогично предыдущему пункту, но относится к пространствам имен.

- **Добавление недостающих точек с запятой.**

- **Справка MSDN** — поиск информации о сообщении об ошибке на сайте MSDN.

  Вы можете либо навести указатель на волнистую линию, чтобы появилась лампочка, либо нажать клавиши CTRL+точка (CTRL+.). Имейте в виду, что при использовании сочетания клавиш курсор не обязательно должен находиться в элементе с ошибкой или в токене. Для получения предложений по любым элементам в строке достаточно, чтобы курсор находился в этой строке.

## <a name="see-also"></a>См. также раздел
 [Setting Language-Specific Editor Options](../../ide/reference/setting-language-specific-editor-options.md) [Refactoring in C++ (VC Blog)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
