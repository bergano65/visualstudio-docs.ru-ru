---
title: Команда Find in Files
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2877057f32ba6553a2cdcefbbc1bb7a8bf2884da
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919256"
---
# <a name="find-in-files-command"></a>Команда Find in Files
Поиск в файлах с использованием набора параметров, доступных на вкладке **Найти в файлах** диалогового окна **Поиск и замена**.

## <a name="syntax"></a>Синтаксис

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Аргументы

`findwhat`\
Обязательный. Текст для поиска совпадения.

## <a name="switches"></a>Переключатели
/case или /c\
Необязательный параметр. Совпадение происходит только в том случае, если прописные и строчные знаки точно соответствуют тем, что указаны в аргументе `findwhat`.

/ext: `extensions`\
Необязательный параметр. Определяет расширения файлов, в которых будет проводиться поиск. Если переключатель не определен, используется предыдущее расширение, вводившееся ранее.

/lookin: `searchpath`\
Необязательный параметр. Каталог, в котором будет производиться поиск. Если путь содержит пробелы, необходимо заключить полный путь в кавычки.

/names или /n\
Необязательный параметр. Отображает список имен файлов, содержащих совпадения.

/options или /t\
Необязательный параметр. Отображает список текущих параметров поиска, но не выполняет сам поиск.

/regex или /r\
Необязательный параметр. Использует стандартные специальные символы в аргументе `findwhat` для представления текстовых шаблонов вместо самих букв. Полный список знаков регулярных выражений см. в разделе [Регулярные выражения](../../ide/using-regular-expressions-in-visual-studio.md).

/reset или /e\
Необязательный параметр. Для параметров поиска возвращает их значения по умолчанию, но не выполняет сам поиск.

/stop\
Необязательный параметр. Останавливает выполнение текущей активной операции поиска. Если указан аргумент `/stop`, остальные аргументы при поиске игнорируются. Например, чтобы остановить текущий поиск, следует ввести следующую строку:

```cmd
>Edit.FindinFiles /stop
```

/sub или /s\
Необязательный параметр. Выполняет поиск в папках, вложенных в каталог, который указан в аргументе /lookin:`searchpath`.

/text2 или /2\
Необязательный параметр. Отображает результаты поиска в окне "Результаты поиска 2".

/wild или /l\
Необязательный параметр. Использует стандартные специальные символы в аргументе `findwhat` для представления символа или последовательности символов.

/word или /w\
Необязательный параметр. Выполняет поиск только целых слов.

## <a name="example"></a>Пример
В данном примере осуществляется поиск "btnCancel" во всех CLS-файлах, расположенных в папке My Visual Studio Projects, а в окне "Результаты поиска 2" отображаются сведения о найденных совпадениях.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>См. также

- [Поиск в файлах](../../ide/find-in-files.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)