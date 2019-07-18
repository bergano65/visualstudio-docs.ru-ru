---
title: IDiaLoadCallback2::RestrictReferencePathAccess | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a39186cfc8fb3f83986692ebf7c608b895aae7ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839736"
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
Определяет, разрешено при поиске PDB-файл в каталоге, где находится файл .exe.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT RestrictReferencePathAccess();
```

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Любой код возврата не `S_OK` во избежание поиск PDB-файл в путь, где находится файл .exe.

## <a name="see-also"></a>См. также
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)