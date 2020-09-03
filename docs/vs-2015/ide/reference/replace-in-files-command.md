---
title: Команда "Заменить в файлах" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d5088366548c9f92d04f1b65a3afc378db29d6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665607"
---
# <a name="replace-in-files-command"></a>Команда Replace In Files
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Заменяет текст в файлах с использованием подмножества параметров, доступных на вкладке **Заменить в файлах** окна **Поиск и замена**.

## <a name="syntax"></a>Синтаксис

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>Аргументы
 `findwhat` Обязательный. Текст для поиска совпадения.

 `replacewith` Обязательный. Текст для замены совпавшего текста.

## <a name="switches"></a>Коммутаторы
 /ALL или/a необязательный. Заменяет все вхождения искомого текста на замещающий текст.

 /case или /c Необязательный. Совпадение происходит только в том случае, если прописные и строчные знаки точно соответствуют тем, что указаны в аргументе `findwhat`.

 /ext: `extensions` Необязательный. Определяет расширения файлов, в которых будет проводиться поиск.

 /КИП или/k необязательный. Указывает, что все измененные файлы остаются открытыми.

 /lookin: `searchpath` Необязательный. Каталог, в котором будет производиться поиск. Если путь содержит пробелы, необходимо заключить полный путь в кавычки.

 /options или /t Необязательный. Отображает список текущих параметров поиска, но не выполняет сам поиск.

 /regex или /r Необязательный. Использует стандартные специальные символы в аргументе `findwhat` для представления текстовых шаблонов вместо самих букв. Полный список знаков регулярных выражений см. в разделе [Регулярные выражения](../../ide/using-regular-expressions-in-visual-studio.md).

 /reset или /e Необязательный. Для параметров поиска возвращает их значения по умолчанию, но не выполняет сам поиск.

 /stop Необязательный. Останавливает выполнение текущей активной операции поиска. Если указан аргумент `/stop`, остальные аргументы при замене игнорируются. Например, чтобы остановить текущую замену, нужно ввести следующую строку:

```
>Edit.ReplaceinFiles /stop
```

 /sub или /s Необязательный. Выполняет поиск в папках, вложенных в каталог, который указан в аргументе /lookin:`searchpath`.

 /text2 или /2 Необязательный. Отображает результаты замены в окне **Результаты поиска 2**.

 /wild или /l Необязательный. Использует стандартные специальные символы в аргументе `findwhat` для представления символа или последовательности символов.

 /word или /w Необязательный. Выполняет поиск только целых слов.

## <a name="example"></a>Пример
 Этот пример ищет `btnCancel` и заменяет на `btnReset` во всех CLS-файлах, расположенных в папке "my visual studio projects", а также отображает сведения о заменах в окне **Результаты поиска 2**.

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>См. также:
 [Поиск и замена текста](../../ide/finding-and-replacing-text.md) ["заменить в файлах](../../ide/replace-in-files.md) " [командное окно](../../ide/reference/command-window.md) ["Поиск/команда"](../../ide/find-command-box.md) в [Visual Studio командные](../../ide/reference/visual-studio-commands.md) [псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
