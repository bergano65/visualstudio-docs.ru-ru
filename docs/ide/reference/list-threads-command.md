---
title: "Команда \"Вывести потоки\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fa71ec1c6eb8ac50d957782dda02a2c3fb59a3c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="list-threads-command"></a>Команда List Threads
Отображает список потоков в текущей программе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>Аргументы  
 `index`  
 Необязательно. Выбирает по индексу поток для использования в качестве текущего.  
  
## <a name="remarks"></a>Примечания  
 Если параметр указан, аргумент `index` помечает указанный поток в качестве текущего. Рядом с текущим потоком в списке отображается звездочка (*).  
  
## <a name="example"></a>Пример  
  
```  
>Debug.ListThreads   
```  
  
## <a name="see-also"></a>См. также  
 [Команда "Вывести стек вызовов"](../../ide/reference/list-call-stack-command.md)   
 [Команда List Disassembly](../../ide/reference/list-disassembly-command.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)