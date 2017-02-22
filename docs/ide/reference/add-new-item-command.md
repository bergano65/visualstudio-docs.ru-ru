---
title: "Команда Add New Item | Microsoft Docs"
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
  - "project.addnewitem"
helpviewer_keywords: 
  - "Добавить новый элемент - команда"
  - "File.AddNewItem - команда"
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Команда Add New Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Добавление к текущему решению нового элемента, например HTM, CSS, TXT или набора рамок, и открытие добавленного элемента.  
  
## Синтаксис  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## Аргументы  
 `filename`  
 Необязательный.  Путь и имя файла элемента, который необходимо добавить в решение.  
  
## Переключатели  
 \/t: `templatename`  
 Необязательный.  Указывает тип создаваемого файла.  Если имя шаблона не задано, по умолчанию создается текстовый файл.  
  
 В синтаксической структуре аргумента \/t:`templatename` используются данные, находящиеся в диалоговом окне **Добавление нового элемента решения**.  Пользователь должен ввести полную категорию, затем тип файла, отделив имя категории от типа файла обратной косой чертой \(`\`\) и заключив всю строку в кавычки.  
  
 Например, чтобы создать новый текстовый файл, для аргумента \/t:`templatename` необходимо ввести следующую строку.  
  
```  
/t:"General\Style Sheet"  
```  
  
 \/e: `editorname`  
 Необязательный.  Имя редактора, в котором будет открыт файл.  Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.  
  
 В синтаксической структуре аргумента \/e:`editorname` имена редакторов используются в том виде, в каком они отображаются в **диалоговом окне "Открыть с помощью"**, с заключением в кавычки.  
  
 Например, чтобы открыть таблицу стилей в редакторе исходного кода, необходимо ввести для аргумента \/e:`editorname` следующую строку.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Пример  
 В приведенном примере в текущее решение добавляется новый элемент решения, MyHTMLpg.  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Окно "Команда"](../../ide/reference/command-window.md)   
 [Поле «Поиск\/Команда»](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)