---
title: Команда "Печать" | Документы Майкрософт
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
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e518b3c6ffc3520b408e7c1bfb1fd1703e40a8de
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561017"
---
# <a name="print-command"></a>Команда Print
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [команду Print](https://docs.microsoft.com/visualstudio/ide/reference/print-command).  
  
  
Вычисляет выражение или отображает указанный текст.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Аргументы  
 `text`  
 Обязательно. Вычисляемое выражение или отображаемый текст.  
  
## <a name="remarks"></a>Примечания  
 Вы можете использовать вопросительный знак (?) в качестве псевдонима для этой команды. Таким образом, команда  
  
```  
>Debug.Print expA  
```  
  
 может быть записана в виде  
  
```  
>? expA  
```  
  
 Обе версии этой команды возвращают текущее значение выражения `expA`.  
  
## <a name="example"></a>Пример  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>См. также  
 [Команда "Вычислить оператор"](../../ide/reference/evaluate-statement-command.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



