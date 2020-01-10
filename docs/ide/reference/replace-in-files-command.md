---
title: Команда Replace In Files
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96f7d7ae0ea5eaf0de1a6fa4357e2750cdd8c22e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565478"
---
# <a name="replace-in-files-command"></a>Команда Replace In Files
Заменяет текст в файлах с использованием подмножества параметров, доступных на вкладке **Заменить в файлах** окна **Поиск и замена**.

## <a name="syntax"></a>Синтаксис

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>Аргументы
`findwhat`

Обязательный. Текст для поиска совпадения.

`replacewith`

Обязательный. Текст для замены совпавшего текста.

## <a name="switches"></a>Переключатели
/all или /a

Необязательный элемент. Заменяет все вхождения искомого текста на замещающий текст.

/case или /c

Необязательный элемент. Совпадение происходит только в том случае, если прописные и строчные знаки точно соответствуют тем, что указаны в аргументе `findwhat`.

/ext: `extensions`

Необязательный элемент. Определяет расширения файлов, в которых будет проводиться поиск.

/keep или /k

Необязательный элемент. Указывает, что все измененные файлы остаются открытыми.

/lookin: `searchpath`

Необязательный элемент. Каталог, в котором будет производиться поиск. Если путь содержит пробелы, необходимо заключить полный путь в кавычки.

/options или /t

Необязательный элемент. Отображает список текущих параметров поиска, но не выполняет сам поиск.

/regex или /r

Необязательный элемент. Использует стандартные специальные символы в аргументе `findwhat` для представления текстовых шаблонов вместо самих букв. Полный список знаков регулярных выражений см. в разделе [Регулярные выражения](../../ide/using-regular-expressions-in-visual-studio.md).

/reset или /e

Необязательный элемент. Для параметров поиска возвращает их значения по умолчанию, но не выполняет сам поиск.

/stop

Необязательный элемент. Останавливает выполнение текущей активной операции поиска. Если указан аргумент `/stop`, остальные аргументы при замене игнорируются. Например, чтобы остановить текущую замену, нужно ввести следующую строку:

```
>Edit.ReplaceinFiles /stop
```

/sub или /s

Необязательный элемент. Выполняет поиск в папках, вложенных в каталог, который указан в аргументе /lookin:`searchpath`.

/text2 или /2

Необязательный элемент. Отображает результаты замены в окне **Результаты поиска 2**.

/wild или /l

Необязательный элемент. Использует стандартные специальные символы в аргументе `findwhat` для представления символа или последовательности символов.

/word или /w

Необязательный элемент. Выполняет поиск только целых слов.

## <a name="example"></a>Пример
Этот пример ищет `btnCancel` и заменяет на `btnReset` во всех CLS-файлах, расположенных в папке "my visual studio projects", а также отображает сведения о заменах в окне **Результаты поиска 2**.

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>См. также

- [Поиск и замена текста](../../ide/finding-and-replacing-text.md)
- [Заменить в файлах](../../ide/replace-in-files.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
