---
title: Перенос по словам
ms.date: 11/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fc38d1ee5a8e5543675700c35cc0cb298aefad9
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349118"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Практическое руководство. Управление переносом слов в редакторе

Флажок **Перенос по словам** можно устанавливать и снимать. Если этот флажок установлен, часть длинной строки, выступающая за пределы текущей ширины окна редактора кода, отображается на следующей строке. Если этот флажок снят, например для упрощения использования нумерации строк, окно можно прокрутить вправо, чтобы увидеть окончание длинной строки.

> [!NOTE]
> Этот раздел относится только к Visual Studio в Windows. Сейчас Visual Studio для Mac не поддерживает перенос по словам.

## <a name="to-set-word-wrap-preferences"></a>Задание настроек переноса по словам

1.  В меню **Сервис** выберите пункт **Параметры**.

2.  В папке **Текстовый редактор** в подпапке **Все языки** выберите **общие** параметры, чтобы задать этот параметр глобально.

     Или...

     Выберите **общие** параметры в подпапке языка программирования.

3.  В разделе **Параметры**установите или снимите флажок **Перенос по словам**.

     Если установлен флажок **Перенос по словам**, включается параметр **Показывать графические метки в местах переноса слов**.

4.  Установите флажок **Показывать графические метки в местах переноса слов**, если требуется отображать стрелку переноса каретки там, где длинная строка переносится на следующую строку. Снимите этот флажок, если не требуется отображать эти стрелки.

    > [!NOTE]
    > Эти стрелки-напоминания не добавляются в код: они отображаются просто для удобства.

## <a name="known-issues"></a>Известные проблемы

Если вы знакомы с переносом слов в Notepad ++, Sublime Text или Visual Studio Code, необходимо учитывать следующие моменты, когда Visual Studio работает не так, как другие редакторы.

* [Тройной щелчок не выделяет всю строку](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [Команда вырезания не удаляет всю строку](https://developercommunity.visualstudio.com/content/problem/138259/cut-command-should-delete-logical-line.html)
* [Двойное нажатие клавиши END не перемещает курсор в конец строки](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>См. также

- [Настройка редактора](../../ide/customizing-the-editor.md)
- [Диалоговое окно "Параметры текстового редактора"](../../ide/reference/text-editor-options-dialog-box.md)
- [Возможности редактора кода](../../ide/writing-code-in-the-code-and-text-editor.md)
