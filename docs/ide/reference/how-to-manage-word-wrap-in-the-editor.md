---
title: Перенос по словам
description: Сведения о включении и отключении переноса по словам в редакторе кода.
ms.custom: SEO-VS-2020
ms.date: 11/07/2018
ms.topic: how-to
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 57e218dadfe04d8cad034f2638ffefb9346e5a41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894599"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Практическое руководство. Управление переносом слов в редакторе

Флажок **Перенос по словам** можно устанавливать и снимать. Если этот флажок установлен, часть длинной строки, выступающая за пределы текущей ширины окна редактора кода, отображается на следующей строке. Если этот флажок снят, например для упрощения использования нумерации строк, окно можно прокрутить вправо, чтобы увидеть окончание длинной строки.

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Сведения по Visual Studio для Mac см. в разделе [Редактор исходного кода: перенос по словам](/visualstudio/mac/source-editor#word-wrap).

## <a name="to-set-word-wrap-preferences"></a>Задание настроек переноса по словам

1. В меню **Сервис** выберите пункт **Параметры**.

2. В папке **Текстовый редактор** в подпапке **Все языки** выберите **общие** параметры, чтобы задать этот параметр глобально.

     Или...

     Выберите **общие** параметры в подпапке языка программирования.

3. В разделе **Параметры** установите или снимите флажок **Перенос по словам**.

     Если установлен флажок **Перенос по словам**, включается параметр **Показывать графические метки в местах переноса слов**.

4. Установите флажок **Показывать графические метки в местах переноса слов**, если требуется отображать стрелку переноса каретки там, где длинная строка переносится на следующую строку. Снимите этот флажок, если не требуется отображать эти стрелки.

    > [!NOTE]
    > Эти стрелки-напоминания не добавляются в код: они отображаются просто для удобства.

## <a name="known-issues"></a>Известные проблемы

Если вы знакомы с переносом слов в Notepad ++, Sublime Text или Visual Studio Code, необходимо учитывать следующие моменты, когда Visual Studio работает не так, как другие редакторы.

* [Тройной щелчок не выделяет всю строку](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [Двойное нажатие клавиши END не перемещает курсор в конец строки](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>См. также

- [Возможности редактора кода](../../ide/writing-code-in-the-code-and-text-editor.md)
