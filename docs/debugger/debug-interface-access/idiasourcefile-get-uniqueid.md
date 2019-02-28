---
title: IDiaSourceFile::get_uniqueId | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_uniqueId method
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4a204e04c1c99dcbe8c6ba6d5e3457ca875dde4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612794"
---
# <a name="idiasourcefilegetuniqueid"></a>IDiaSourceFile::get_uniqueId
Извлекает значение ключа простым целым числом, которое является уникальным для этого образа.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_uniqueId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает значение ключа простым целым числом, которое является уникальным для этого образа.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Сравнении ключей, а не строк могут ускорить обработка номеров строк.

## <a name="see-also"></a>См. также раздел
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)