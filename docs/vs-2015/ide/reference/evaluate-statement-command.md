---
title: Команда "Вычислить оператор" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 54f581b710777cf4548115e76580be552e4e7520
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54800699"
---
# <a name="evaluate-statement-command"></a>Команда Evaluate Statement
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Вычисляет и отображает заданный оператор.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.EvaluateStatement text   
```  
  
## <a name="arguments"></a>Аргументы  
 `text`  
 Обязательный. Вычисляемый оператор.  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [Команда "Печать"](../../ide/reference/print-command.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
