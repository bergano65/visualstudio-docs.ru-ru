---
title: Как отладить нарушение доступа C++ | Документы Майкрософт
ms.custom: ''
ms.date: 05/23/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 24d3eed91a659dc8f0d114369bdba45dd2973375
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-can-i-debug-a-c-access-violation"></a>Как отладить нарушение доступа C++
## <a name="problem-description"></a>Описание проблемы  
 Программа порождает нарушение доступа. Как это отладить?  
  
## <a name="solution"></a>Решение  
 Если вы получаете нарушение прав доступа в строке кода, которая разыменовывает несколько указателей, может быть трудно определить указатель, который вызвал нарушение прав доступа. Начиная с Visual Studio 2015 с обновлением 1 диалоговое окно исключения теперь явно называет указатель, который вызвал нарушение прав доступа.  
  
 Например, если имеется следующий код, вы должны получить нарушение прав доступа:  
  
```C++  
#include <iostream>  
using namespace std;  
  
class ClassB {  
public:  
        ClassC* C;  
        ClassB() {  
                C = new ClassC();  
        }  
     void printHello() {  
                cout << "hello world";  
        }  
};  
  
class ClassA {  
public:  
    ClassB* B;  
      ClassA() {  
                B = nullptr;  
        }  
};  
  
int main() {  
    ClassA* A = new ClassA();  
      A->B->printHello();  
}  
```  
  
 При выполнении этого кода в Visual Studio 2015 с обновлением 1 вы увидите следующее диалоговое окно исключения:  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 Если не удается определить, почему указатель вызвал нарушение прав доступа, выполните трассировку кода, чтобы проверить правильность назначения указателя, ставшего причиной проблемы.  Если он передается как параметр, убедитесь, что он передается правильно, и вы не создаете случайно [shallow копирования](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). Затем убедитесь, что значения не изменяются непреднамеренно где-нибудь в программе путем создания точки останова по данным для указателя рассматриваемой убедитесь, что он не изменяется в другом месте программы. Дополнительные сведения о точках останова по данным см. в разделе, посвященном точкам останова по данным, в статье [Using Breakpoints](../debugger/using-breakpoints.md).  
  
## <a name="see-also"></a>См. также  
 [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)