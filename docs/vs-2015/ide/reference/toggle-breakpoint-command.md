---
title: Команда Toggle Breakpoint | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 11f0598fa20a5293d662bdbb23b7f67c6c0c80b2
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54793178"
---
# <a name="toggle-breakpoint-command"></a>Команда Toggle Breakpoint
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Включает или отключает точку останова в зависимости от ее текущего состояния и текущей позиции в файле.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## <a name="arguments"></a>Аргументы  
 `text`  
 Необязательный параметр. Если текст указан, строка помечается как именованная точка останова. В противном случае строка помечается как неименованная точка останова, что аналогично нажатию клавиши F9.  
  
## <a name="example"></a>Пример  
 В этом примере переключается текущая точка останова.  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
