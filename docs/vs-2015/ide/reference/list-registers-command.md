---
title: Команда "Вывести регистры" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6f9eaa1299ec49cf20713723e822f8fc641401d8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199134"
---
# <a name="list-registers-command"></a>Команда List Registers
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отображает значение выбранных регистров и позволяет изменить список отображаемых регистров.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## <a name="switches"></a>Переключатели  
 /Display [{`register`&#124;`registerGroup`}...]  
 Отображает значения указанного `register` или `registerGroup`. Если `register` или `registerGroup` не задан, отображается список регистров по умолчанию. Аналогичное поведение применяется при отсутствии заданных параметров. Например:  
  
 `Debug.ListRegisters /Display eax`  
  
 эквивалентно  
  
 `Debug.ListRegisters eax`  
  
 /List  
 Отображает все группы регистров в списке.  
  
 /Watch [{`register`&#124;`registerGroup`}...]  
 Добавляет одно или несколько значений `register` или `registerGroup` в список.  
  
 /Unwatch [{`register`&#124;`registerGroup`}...]  
 Удаляет одно или несколько значений `register` или `registerGroup` из списка.  
  
## <a name="remarks"></a>Примечания  
 Вместо `Debug.ListRegisters` можно использовать псевдоним `r`.  
  
## <a name="example"></a>Пример  
 Этот пример использует псевдоним `r` для `Debug.ListRegisters`, чтобы отобразить значения группы регистров `Flags`.  
  
```  
r /Display Flags  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Общие сведения об отладке: Окно "Регистры"](../../debugger/debugging-basics-registers-window.md)   
 [Практическое руководство. Использование окна регистров](../../debugger/how-to-use-the-registers-window.md)
