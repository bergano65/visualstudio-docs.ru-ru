---
title: Команда "Открыть решение" | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e97fa5265550222b4df9143a900419a0994f9129
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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