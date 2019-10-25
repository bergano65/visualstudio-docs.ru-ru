---
title: 'IDiaLoadCallback2:: Рестрикторигиналпасакцесс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bcdaa7c1896a0ef29706e3650ad8ac56537f778
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743003"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Определяет, можно ли искать PDB-файл в исходном каталоге отладки.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Любой код возврата, отличный от `S_OK`, не делает поиск PDB-файла в исходном каталоге отладки. Исходный каталог отладки — это путь к файлу символов, скомпилированному в исполняемый файл при включенной отладке. Этот путь не обязательно должен совпадать с путем, в котором существует исполняемый файл.

## <a name="see-also"></a>См. также
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)