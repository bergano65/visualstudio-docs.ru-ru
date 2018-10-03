---
title: Команда Toggle Breakpoint | Документы Майкрософт
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
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c7dd3bd7a4d42b8135aed034464223af53091f87
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557922"
---
# <a name="toggle-breakpoint-command"></a>Команда Toggle Breakpoint
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [команда Toggle Breakpoint](https://docs.microsoft.com/visualstudio/ide/reference/toggle-breakpoint-command).  
  
  
Включает или отключает точку останова в зависимости от ее текущего состояния и текущей позиции в файле.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## <a name="arguments"></a>Аргументы  
 `text`  
 Необязательный. Если текст указан, строка помечается как именованная точка останова. В противном случае строка помечается как неименованная точка останова, что аналогично нажатию клавиши F9.  
  
## <a name="example"></a>Пример  
 В этом примере переключается текущая точка останова.  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



