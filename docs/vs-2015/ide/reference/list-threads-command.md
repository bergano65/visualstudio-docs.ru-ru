---
title: Команда "Вывести потоки" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 90aff3fb3d3cbb596708bde1db8ff171198a5a60
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199104"
---
# <a name="list-threads-command"></a>Команда List Threads
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отображает список потоков в текущей программе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>Аргументы  
 `index`  
 Необязательный параметр. Выбирает по индексу поток для использования в качестве текущего.  
  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
