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
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56595363"
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

## <a name="see-also"></a>См. также раздел
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)