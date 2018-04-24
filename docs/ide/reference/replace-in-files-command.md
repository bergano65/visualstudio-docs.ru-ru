---
title: Команда "Заменить в файлах" | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fcf12ba2c439e9ecb77aeecf47e7fe4fc535b4aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
 Обязательно. Текст для поиска совпадения.  
  
 `replacewith`  
 Обязательно. Текст для замены совпавшего текста.  
  
## <a name="switches"></a>Переключатели  
 /all или /a  
 Необязательный. Заменяет все вхождения искомого текста на замещающий текст.  
  
 /case или /c  
 Необязательный. Совпадение происходит только в том случае, если прописные и строчные знаки точно соответствуют тем, что указаны в аргументе `findwhat`.  
  
 /ext: `extensions`  
 Необязательный. Определяет расширения файлов, в которых будет проводиться поиск.  
  
 /keep или /k  
 Необязательный. Указывает, что все измененные файлы остаются открытыми.  
  
 /lookin: `searchpath`  
 Необязательный. Каталог, в котором будет производиться поиск. Если путь содержит пробелы, необходимо заключить полный путь в кавычки.  
  
 /options или /t  
 Необязательный. Отображает список текущих параметров поиска, но не выполняет сам поиск.  
  
 /regex или /r  
 Необязательный. Использует стандартные специальные символы в аргументе `findwhat` для представления текстовых шаблонов вместо самих букв. Полный список знаков регулярных выражений см. в разделе [Регулярные выражения](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /reset или /e  
 Необязательный. Для параметров поиска возвращает их значения по умолчанию, но не выполняет сам поиск.  
  
 /stop  
 Необязательный. Останавливает выполнение текущей активной операции поиска. Если указан аргумент `/stop`, остальные аргументы при замене игнорируются. Например, чтобы остановить текущую замену, нужно ввести следующую строку:  
  
```  
>Edit.ReplaceinFiles /stop  
```  
  
 /sub или /s  
 Необязательный. Выполняет поиск в папках, вложенных в каталог, который указан в аргументе /lookin:`searchpath`.  
  
 /text2 или /2  
 Необязательный. Отображает результаты замены в окне **Результаты поиска 2**.  
  
 /wild или /l  
 Необязательный. Использует стандартные специальные символы в аргументе `findwhat` для представления символа или последовательности символов.  
  
 /word или /w  
 Необязательный. Выполняет поиск только целых слов.  
  
## <a name="example"></a>Пример  
 Этот пример ищет `btnCancel` и заменяет на `btnReset` во всех CLS-файлах, расположенных в папке "my visual studio projects", а также отображает сведения о заменах в окне **Результаты поиска 2**.  
  
```  
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2  
```  
  
## <a name="see-also"></a>См. также  
 [Поиск и замена текста](../../ide/finding-and-replacing-text.md)   
 [Заменить в файлах](../../ide/replace-in-files.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)