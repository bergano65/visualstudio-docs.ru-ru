---
title: Команда Toggle Breakpoint | Документы Майкрософт
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
ms.openlocfilehash: f993d9a0377531b155301bed235c00bf8e6667c4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223162"
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



