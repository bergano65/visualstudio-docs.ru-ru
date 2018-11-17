---
title: Функции-ловушки клиентского блока | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 2b16dc9eaff974e98e411d4f49d8aed6f9f656e8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773942"
---
# <a name="client-block-hook-functions"></a>Функции-ловушки клиентского блока
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если нужно проверить или вывести данные, хранящиеся в блоках типа `_CLIENT_BLOCK`, можно написать для этого специальную функцию. Эта функция должна иметь прототип наподобие следующего, определенного в CRTDBG.H:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 Другими словами, функция-ловушка должна принимать **void** указатель на начало блока выделения, вместе с **size_t** введите значение, показывающее размер выделения и возвращать `void`. Все остальное задается по желанию.  
  
 После установки функции ловушек с помощью [_CrtSetDumpClient](http://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033), он будет вызываться каждый раз `_CLIENT_BLOCK` дампе блока. Затем можно использовать [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) для получения сведений о типе или подтипе выводимых блоков.  
  
 Указатель на функцию, который передается `_CrtSetDumpClient` имеет тип **_CRT_DUMP_CLIENT**, как определено в CRTDBG. H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>См. также  
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
 [Образец crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)



