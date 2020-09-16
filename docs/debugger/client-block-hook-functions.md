---
title: Функции-ловушки клиентского блока | Документация Майкрософт
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 881809dda7e8254f9d337b68f0c317eccfd9093d
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600206"
---
# <a name="client-block-hook-functions"></a>Функции-ловушки клиентского блока
Если нужно проверить или вывести данные, хранящиеся в блоках типа `_CLIENT_BLOCK`, можно написать для этого специальную функцию. Эта функция должна иметь прототип наподобие следующего, определенного в CRTDBG.H:

```cpp
void YourClientDump(void *, size_t)
```

 Другими словами, функция-ловушка должна принимать указатель типа **void** на начало блока выделения и значение типа **size_t**, показывающее размер выделения, и возвращать тип `void`. Все остальное задается по желанию.

 Один раз установленная с помощью[_CrtSetDumpClient`_CLIENT_BLOCK`, функция-ловушка будет вызываться всякий раз при дампе блока ](/cpp/c-runtime-library/reference/crtsetdumpclient). [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) можно применять для получения сведений о типе или подтипе выводимых блоков.

 Указатель на функцию, который передается `_CrtSetDumpClient`, имеет тип **_CRT_DUMP_CLIENT**, как определено в CRTDBG.H:

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>См. также

- [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)
- [Пример crt_dbg2](/previous-versions/b31tft51(v=vs.100))
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)