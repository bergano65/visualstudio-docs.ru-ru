---
title: "Команда Toggle Breakpoint | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b21255b33718e79031c037d1339343c9fe884ce3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="toggle-breakpoint-command"></a>Команда Toggle Breakpoint
Включает или отключает точку останова в зависимости от ее текущего состояния и текущей позиции в файле.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## <a name="arguments"></a>Аргументы  
 `text`  
 Необязательно. Если текст указан, строка помечается как именованная точка останова. В противном случае строка помечается как неименованная точка останова, что аналогично нажатию клавиши F9.  
  
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