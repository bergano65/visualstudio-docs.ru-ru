---
title: Функции-ловушки клиентского блока | Документация Майкрософт
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
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3eb0891911e5dacbad2447ba3d141a81286e7dc8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991842"
---
# <a name="client-block-hook-functions"></a>Функции-ловушки клиентского блока
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если нужно проверить или вывести данные, хранящиеся в блоках типа `_CLIENT_BLOCK`, можно написать для этого специальную функцию. Эта функция должна иметь прототип наподобие следующего, определенного в CRTDBG.H:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 Другими словами, функция-ловушка должна принимать указатель типа **void** на начало блока выделения и значение типа **size_t**, показывающее размер выделения, и возвращать тип `void`. Все остальное задается по желанию.  
  
 Один раз установленная с помощью[_CrtSetDumpClient`_CLIENT_BLOCK`, функция-ловушка будет вызываться всякий раз при дампе блока ](http://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033). [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) можно применять для получения сведений о типе или подтипе выводимых блоков.  
  
 Указатель на функцию, который передается `_CrtSetDumpClient`, имеет тип **_CRT_DUMP_CLIENT**, как определено в CRTDBG.H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>См. также  
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
 [Образец crt_dbg2](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)
