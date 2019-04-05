---
title: Функции-ловушки выделения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d8d2aff47737443b998cfae8d16c3d95a5eb1d2a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993422"
---
# <a name="allocation-hook-functions"></a>Функции-ловушки выделения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Функции-ловушки выделения, установленные с помощью [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d), вызываются всякий раз при выделении, перераспределении или освобождении памяти. Этот тип ловушек может применяться для различных целей. Используйте их, например, для проверки, как приложение обрабатывает ситуации недостатка памяти, или для оценки шаблонов выделения, или для регистрации данных о выделении для дальнейшего анализа.  
  
> [!NOTE]
>  Следует знать об ограничениях функций библиотеки CRT в функциях-ловушках выделения, описанных в разделе [Ловушки выделения и выделения памяти CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Функция-ловушка выделения должна иметь следующий прототип:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Указатель, который передается [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d), имеет тип **_CRT_ALLOC_HOOK**, как определено в CRTDBG.H:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Когда библиотека CRT вызывает ловушку, *nAllocType* аргумент указывает, какие выделения операция будет выполняться (**_HOOK_ALLOC**, **_HOOK_REALLOC**, или **_HOOK_FREE**). В случае освобождения или перераспределения, `pvData` содержит указатель на пользовательскую часть освобождаемого блока. Однако в случае выделения памяти этот указатель пуст, так как выделение еще не произошло. Остальные аргументы содержат размер запрашиваемого выделения, его тип блока, номер последующего запроса, связанный с выделением запроса, и указатель на имя файла и номер строки, в которой было сделано выделение (если доступно). После того как функция-ловушка выполнит анализ и другие запрограммированные автором действия, она должна вернуть или значение **TRUE**, означающее, что операция выделения может продолжаться, или значение **FALSE** в случае предполагаемого сбоя операции. Простая ловушка этого типа может проверить количество выделенной до настоящего момента памяти и вернуть **FALSE** в случае превышения лимита. В таком случае в приложении могут возникать ошибки выделения памяти, которые обычно возникают только при большой нехватке доступной памяти. Более сложные ловушки могут отслеживать структуру выделения, анализировать использование памяти или сообщать о возникновении какой-либо определенной ситуации.  
  
## <a name="see-also"></a>См. также  
 [Ловушки выделения и выделения памяти CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
 [Образец crt_dbg2](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
