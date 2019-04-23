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
ms.openlocfilehash: 5a57f02a7c1b9845f4248daf2282b6f285f95489
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666342"
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
