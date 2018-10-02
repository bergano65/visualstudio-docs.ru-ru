---
title: Команда "Вывести потоки" | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cd8e9f96e0f477ba0b83419274d9b2ed0a101195
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569745"
---
# <a name="list-threads-command"></a>Команда List Threads
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [команда List Threads](https://docs.microsoft.com/visualstudio/ide/reference/list-threads-command).  
  
  
Отображает список потоков в текущей программе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>Аргументы  
 `index`  
 Необязательный. Выбирает по индексу поток для использования в качестве текущего.  
  
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



