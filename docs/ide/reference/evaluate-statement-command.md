---
title: "Команда \"Вычислить оператор\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b3f0d5ecdcf1318490ac0829bb9dd6ded9519872
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="evaluate-statement-command"></a>Команда Evaluate Statement
Вычисляет и отображает заданный оператор.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.EvaluateStatement text   
```  
  
## <a name="arguments"></a>Аргументы  
 `text`  
 Обязательно. Вычисляемый оператор.  
  
## <a name="remarks"></a>Примечания  
 Окно, используемое для ввода команды **EvaluateStatement**, определяет, интерпретируется ли знак равенства (=) как оператор сравнения или оператор присваивания.  
  
 В **командном окне** знак равенства (=) интерпретируется как оператор сравнения. Например, если значения переменных `a` и `b` различаются, то команда  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 возвращает значение `false`.  
  
 В окне **интерпретации**, напротив, знак равенства (=) интерпретируется как оператор присваивания. Таким образом, команда  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 присвоит переменной `a` значение переменной `b`.  
  
## <a name="example"></a>Пример  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## <a name="see-also"></a>См. также  
 [Команда "Печать"](../../ide/reference/print-command.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)