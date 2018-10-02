---
title: Оператор Stop в Visual Basic | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fcb4e3018dad53ef869748a4394363dba78f71c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557798"
---
# <a name="stop-statements-in-visual-basic"></a>Оператор Stop в Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [операторы Stop в Visual Basic](https://docs.microsoft.com/visualstudio/debugger/stop-statements-in-visual-basic).  
  
Оператор "Stop" в Visual Basic является программной альтернативой заданию точки останова. Когда отладчик встречает оператор "Stop", он прерывает выполнение программы (переходит в режим приостановки выполнения). Программисты C# могут добиться того же результата с помощью вызова System.Diagnostics.Debugger.Break.  
  
 Оператор "Stop" задается и удаляется путем редактирования исходного кода. В отличие от точки останова его невозможно задать или удалить с помощью команд отладчика.  
  
 В отличие от оператора "End" оператор "Stop" не сбрасывает значения переменных и не переводит приложение в режим разработки. Для продолжения выполнения приложения можно выбрать пункт "Продолжить" в меню "Отладка".  
  
 В случае запуска приложения Visual Basic вне отладчика оператор "Stop" запустит отладчик, если включена JIT–отладка. Если же JIT–отладка не включена, оператор "Stop" приведет к завершению работы приложения, как если бы это был оператор "End". При этом события "QueryUnload" и "Unload" не возникают, поэтому в выпускаемой версии приложения Visual Basic необходимо удалить все операторы "Stop". Дополнительные сведения см. в разделе [JIT-отладка](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Чтобы избежать необходимости удаления операторов "Stop", можно использовать условную компиляцию:  
  
```  
#If DEBUG Then  
   Stop  
#Else  
   ' Don't stop  
#End If  
```  
  
 Другой вариант — воспользоваться оператором "Assert" вместо оператора "Stop". Оператор "Debug.Assert" прерывает выполнение программы только в том случае, если не выполнено заданное условие, и автоматически удаляется при построении выпускаемой версии приложения. Дополнительные сведения см. в разделе [утверждения в управляемом коде](../debugger/assertions-in-managed-code.md). Если требуется, чтобы оператор "Assert" всегда прерывал выполнение программы в отладочной версии, его можно задать следующим образом:  
  
```  
Debug.Assert(false)  
```  
  
 И еще один вариант — использовать метод Debug.Fail:  
  
```  
Debug.Fail("a clever output string goes here")  
```  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)



