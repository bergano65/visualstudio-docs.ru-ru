---
title: Команда "Открыть решение" | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 15c51e341761ad34241f1230f797896ce8dc2e9e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186424"
---
# <a name="open-solution-command"></a>Команда Open Solution
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



