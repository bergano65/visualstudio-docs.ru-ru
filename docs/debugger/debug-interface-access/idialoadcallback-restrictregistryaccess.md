---
title: IDiaLoadCallback::RestrictRegistryAccess | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictRegistryAccess method
ms.assetid: de4760c3-a746-4bab-8065-1388fed31b67
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25e6397b65c717be65a9a707dd0a53fc70321acb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828502"
---
# <a name="idialoadcallbackrestrictregistryaccess"></a>IDiaLoadCallback::RestrictRegistryAccess
Определяет, если запросы реестра могут использоваться для поиска пути поиска символов.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT RestrictRegistryAccess();
```

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Любой код возврата не `S_OK` предотвращает запроса из реестра для пути поиска символов.

## <a name="see-also"></a>См. также
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)