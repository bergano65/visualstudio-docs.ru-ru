---
title: "Команда Replace In Files | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.replaceinfiles"
helpviewer_keywords: 
  - "Edit.ReplaceInFiles - команда"
  - "Заменить в файлах - команда"
  - "ReplaceInFiles - команда"
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Команда Replace In Files
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Замена текста в файлах с помощью подмножества параметров, доступных на вкладке **Заменить в файлах** диалогового окна **Поиск и замена**.  
  
## Синтаксис  
  
```  
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]  
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]  
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]  
```  
  
## Аргументы  
 `findwhat`  
 Обязательный.  Текст для поиска совпадения.  
  
 `replacewith`  
 Обязательный.  Текст, заменяемый совпадающим текстом.  
  
## Переключатели  
 \/all или \/a  
 Необязательный.  Во всех случаях вхождения искомого текста он заменяется замещающим текстом.  
  
 \/case или \/c  
 Необязательный.  Совпадение происходит только в том случае, если прописные и строчные знаки точно соответствуют тем, что указаны в аргументе `findwhat`.  
  
 \/ext: `extensions`  
 Необязательный.  Определяет расширения файлов, в которых будет проводиться поиск.  
  
 \/keep или \/k  
 Необязательный.  Указывает, что все изменяемые файлы остаются открытыми.  
  
 \/lookin: `searchpath`  
 Необязательный.  Каталог, в котором будет производиться поиск.  Если путь содержит пробелы, необходимо заключить полный путь в кавычки.  
  
 \/options или \/t  
 Необязательный.  Отображает список текущих параметров поиска, но не выполняет сам поиск.  
  
 \/regex или \/r  
 Необязательный.  Использует стандартные специальные знаки в аргументе `findwhat` для представления текстовых шаблонов вместо самих букв.  Полный список знаков регулярных выражений см. в разделе [Регулярные выражения](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 \/reset или \/e  
 Необязательный.  Для параметров поиска возвращает их значения по умолчанию, но не выполняет сам поиск.  
  
 \/stop  
 Необязательный.  Останавливает выполнение текущей активной операции поиска.  Если указан аргумент `/stop` , остальные аргументы при поиске заменяются.  Например, чтобы остановить текущую замену, следует ввести следующую строку:  
  
```  
>Edit.ReplaceinFiles /stop  
```  
  
 \/sub или \/s  
 Необязательный.  Выполняет поиск в папках, вложенных в каталог, который указан в аргументе \/lookin:`searchpath`.  
  
 \/text2 или \/2  
 Необязательный.  Отображаются результаты замены в окне **Результаты поиска 2**.  
  
 \/wild или \/l  
 Необязательный.  Использует стандартные специальные знаки в аргументе `findwhat` для представления символа или последовательности символов.  
  
 \/word или \/w  
 Необязательный.  Выполняет поиск только целых слов.  
  
## Пример  
 В данном примере выполняется поиск вхождений `btnCancel`, которые заменяются на `btnReset` во всех CLS\-файлах, расположенных в папке "my visual studio projects”, а в окне **Результаты поиска 2** отображаются сведения о выполненных заменах.  
  
```  
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2  
```  
  
## См. также  
 [Поиск и замена текста](../../ide/finding-and-replacing-text.md)   
 [Заменить в файлах](../../ide/replace-in-files.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)