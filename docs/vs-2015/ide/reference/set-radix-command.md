---
title: Команда "Задать основание системы счисления" | Документы Майкрософт
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
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 99b5623fff4e2919bb34bc7dd4ba60d14ba93077
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559148"
---
# <a name="set-radix-command"></a>Команда Set Radix
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [задать основание системы счисления-команда](https://docs.microsoft.com/visualstudio/ide/reference/set-radix-command).  
  
  
Задает или возвращает числовой базовый тип, используемый для отображения целочисленных значений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## <a name="arguments"></a>Аргументы  
 `10` или `16` или `hex` или `dec`  
 Необязательный. Указывает десятичную (10 или dec) или шестнадцатеричную (16 или hex) систему счисления. Если аргумент отсутствует, возвращается основание текущей системы счисления.  
  
## <a name="example"></a>Пример  
 В приведенном примере в среде настраивается отображение целочисленных значений в шестнадцатеричном формате.  
  
```  
>Debug.SetRadix hex  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



