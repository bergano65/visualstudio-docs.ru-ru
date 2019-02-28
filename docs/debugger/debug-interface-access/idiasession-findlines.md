---
title: IDiaSession::findLines | Документация Майкрософт
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
ms.openlocfilehash: b127cbc5c9ddc5a2aa2d293d1371bab18d191fdb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642889"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
Извлекает номера строк в указанной единице компиляции и идентификаторы файлов источника.

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

[in] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий единице компиляции. Этот интерфейс используется как контекст, в котором осуществляется поиск номера строк.

 `file`

[in] [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) объект, представляющий исходный файл, в котором осуществляется поиск номера строк.

 `ppResult`

[out] Возвращает [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) извлечь объект, который содержит список номеров строк.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)