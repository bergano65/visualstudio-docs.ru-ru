---
title: "Команда \"Открыть решение\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a67e3884fbb5e0c4bbb3a5aefe2cdcc8ac7d683e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="open-solution-command"></a>Команда Open Solution
Открывает существующее решение, закрывая все другие открытые решения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
File.OpenSolution filename  
```  
  
## <a name="arguments"></a>Аргументы  
 `Filename`  
 Обязательно. Полный путь и имя файла открываемого решения.  
  
 В соответствии с требованиями синтаксиса для аргумента `filename` путь, содержащий пробелы, должен заключаться в кавычки.  
  
## <a name="remarks"></a>Примечания  
 Функция автозавершения пытается определить правильный путь и правильное имя файла во время их ввода.  
  
## <a name="example"></a>Пример  
 В этом примере открывается решение Test1.sln.  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)