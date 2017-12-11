---
title: "Команда \"Открыть файл\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f7b1576ce7c34e953c45d7b303190a00d77e86cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="open-file-command"></a>Команда Open File
Открывает существующий файл и позволяет указать редактор.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
File.OpenFile filename [/e:editorname]  
```  
  
## <a name="arguments"></a>Аргументы  
 `filename`  
 Обязательный. Полный или частичный путь и имя для открываемого файла. Пути, содержащие пробелы, следует заключить в кавычки.  
  
## <a name="switches"></a>Переключатели  
 /e:`editorname`  
 Необязательно. Имя редактора, в котором будет открыт файл. Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.  
  
 В синтаксической структуре аргумента /e:`editorname` имена редакторов используются в том виде, в каком они отображаются в диалоговом окне "Открыть с помощью", с заключением в кавычки.  
  
 Например, чтобы открыть файл в редакторе исходного кода, нужно ввести для аргумента /e:`editorname` следующую строку:  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="remarks"></a>Примечания  
 Когда вы вводите путь, функция автозавершения пытается определить правильный путь и правильное имя файла.  
  
## <a name="example"></a>Пример  
 Этот пример открывает файл стилей "Test1.CSS" в редакторе исходного кода.  
  
```  
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Окно интерпретации](../../ide/reference/immediate-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)