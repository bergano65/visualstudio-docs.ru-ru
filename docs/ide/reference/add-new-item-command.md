---
title: "Команда \"Добавить новый элемент\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ef0373d148d386d0b725d74ea639f1b8b0719cc3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="add-new-item-command"></a>Команда Add New Item
Добавляет новый элемент решения, такой как HTM, CSS, TXT или набор фреймов, в текущее решение и открывает его.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## <a name="arguments"></a>Аргументы  
 `filename`  
 Необязательный. Путь и имя файла элемента, который необходимо добавить в решение.  
  
## <a name="switches"></a>Переключатели  
 /t: `templatename`  
 Необязательно. Указывает тип создаваемого файла. Если имя шаблона не задано, по умолчанию создается текстовый файл.  
  
 В синтаксической структуре аргумента /t:`templatename` используются данные, находящиеся в диалоговом окне **Добавление нового элемента решения**. Вам необходимо ввести полную категорию, затем тип файла, отделив имя категории от типа файла обратной косой чертой (`\`) и заключив всю строку в кавычки.  
  
 Например, чтобы создать текстовый файл, для аргумента /t:`templatename` необходимо ввести следующую строку:  
  
```  
/t:"General\Style Sheet"  
```  
  
 /e: `editorname`  
 Необязательно. Имя редактора, в котором будет открыт файл. Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.  
  
 В синтаксической структуре аргумента /e:`editorname` имена редакторов используются в том виде, в каком они отображаются в диалоговом окне **Открыть с помощью**, с заключением в кавычки.  
  
 Например, чтобы открыть таблицу стилей в редакторе исходного кода, необходимо ввести для аргумента /e:`editorname` следующую строку:  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="example"></a>Пример  
 В приведенном примере в текущее решение добавляется новый элемент решения MyHTMLpg.  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)