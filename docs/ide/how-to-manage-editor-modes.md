---
title: Полноэкранный режим и режим виртуального пространства Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94bc99bf70340ef76639d0ae0f05e1f7737173a2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-manage-editor-modes"></a>Практическое руководство. Управление режимами редактора

Предусмотрено несколько режимов отображения редактора кода Visual Studio.

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в этой статье в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, например на **Общие** или **Visual C++**, выберите **Сервис** > **Импорт и экспорт параметров**, а затем щелкните **Сбросить все параметры**.

## <a name="enable-full-screen-mode"></a>Включение полноэкранного режима

Включив режим **Во весь экран**, вы можете скрыть все окна инструментов и просматривать только окна документов.

-   Нажмите клавиши **ALT**+**SHIFT**+**ВВОД**, чтобы перейти в режим **Во весь экран** или выйти из него.

     — или —

-   Введите команду `View.Fullscreen` в **командном окне**.

## <a name="enable-virtual-space-mode"></a>Включение режима виртуального пространства

В режиме **виртуального пространства** в конце каждой строки кода вставляются пробелы. Этот параметр позволяет помещать комментарии на одинаковом расстоянии от кода.

1.  В меню **Сервис** выберите пункт **Параметры**.

2.  Разверните папку **Текстовый редактор** и выберите **Все языки**, чтобы задать этот параметр как глобальный. В противном случае выберите папку конкретного языка. Например, чтобы включить нумерацию строк только в Visual Basic, выберите узел **Basic** > **Текстовый редактор**.

3.  Перейдите на вкладку **Общие** и в разделе **Параметры** выберите **Включить виртуальное пространство**.

    > [!NOTE]
    > **Виртуальное пространство** включено в режиме **Выбор столбцов**. Когда режим **виртуального пространства** не включен, точка вставки курсора переходит с конца одной строки непосредственно на первый символ следующей строки.

## <a name="see-also"></a>См. также

- [Настройка редактора](../ide/customizing-the-editor.md)
- [Настройка макетов окон в Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)
- [Страница "Шрифты и цвета", папка "Среда", диалоговое окно "Параметры"](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)