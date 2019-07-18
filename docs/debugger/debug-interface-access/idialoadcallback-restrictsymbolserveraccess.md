---
title: IDiaLoadCallback::RestrictSymbolServerAccess | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictSymbolServerAccess method
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0de567f0417714e1246e11ba074c9b0134e92ce8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839775"
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
Определяет, если доступ разрешен на сервере символов для разрешения символов.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT RestrictSymbolServerAccess();
```

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Любой код возврата не `S_OK` предотвращает использование сервера символов для разрешения символов.

## <a name="see-also"></a>См. также
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)