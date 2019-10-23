---
title: 'IDiaSession:: Финдлинес | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6082bfe8a3eee00d425441ff44a6eadd1c36e27
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742128"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
Получает номера строк в указанных компилируемого объекта и идентификаторах исходных файлов.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findLines ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Параметры
 `compiland`

окне Объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий компилируемого объекта. Используйте этот интерфейс в качестве контекста для поиска номеров строк.

 `file`

окне Объект [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , представляющий исходный файл, в котором выполняется поиск номеров строк.

 `ppResult`

заполняет Возвращает объект [идиаенумлиненумберс](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , содержащий список полученных номеров строк.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)