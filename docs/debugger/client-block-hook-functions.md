---
title: Функции-ловушки клиентского блока | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee0209c082185e111988e5f8e39f2f0b806a4995
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433123"
---
# <a name="client-block-hook-functions"></a>Функции-ловушки клиентского блока
Если нужно проверить или вывести данные, хранящиеся в блоках типа `_CLIENT_BLOCK`, можно написать для этого специальную функцию. Эта функция должна иметь прототип наподобие следующего, определенного в CRTDBG.H:  
  
```cpp
void YourClientDump(void *, size_t)  
  
```  
  
 Другими словами, функция-ловушка должна принимать **void** указатель на начало блока выделения, вместе с **size_t** введите значение, показывающее размер выделения и возвращать `void`. Все остальное задается по желанию.  
  
 После установки функции ловушек с помощью [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), он будет вызываться каждый раз `_CLIENT_BLOCK` дампе блока. Затем можно использовать [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) для получения сведений о типе или подтипе выводимых блоков.  
  
 Указатель на функцию, который передается `_CrtSetDumpClient` имеет тип **_CRT_DUMP_CLIENT**, как определено в CRTDBG. H:  
  
```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>См. также  
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
 [Образец crt_dbg2](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)
