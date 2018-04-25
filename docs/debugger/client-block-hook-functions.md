---
title: Функции-ловушки клиентского блока | Документы Microsoft
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
ms.openlocfilehash: eccc1781174394da333d2fc703fec0b4d31e522a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="client-block-hook-functions"></a>Функции-ловушки клиентского блока
Если нужно проверить или вывести данные, хранящиеся в блоках типа `_CLIENT_BLOCK`, можно написать для этого специальную функцию. Эта функция должна иметь прототип наподобие следующего, определенного в CRTDBG.H:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 Другими словами, функция-ловушка должна принимать **void** указатель на начало блока выделения, вместе с **size_t** введите значение, указывающее размер выделения и возвращать `void`. Все остальное задается по желанию.  
  
 После установки функции ловушек с помощью [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), он будет вызываться каждый раз `_CLIENT_BLOCK` дампе блока. Затем можно использовать [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) для получения сведений о типе или подтипе выводимых блоков.  
  
 Указатель на функцию, которая передается в `_CrtSetDumpClient` относится к типу **_CRT_DUMP_CLIENT**, как определено в CRTDBG. H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>См. также  
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
 [Образец crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)