---
title: IDiaEnumSourceFiles::Clone | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Clone method
ms.assetid: 87a9a9b6-3927-4131-927c-ad95f8f098b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 328536b64bdea2591b4ab8c242348b8304984466
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624637"
---
# <a name="idiaenumsourcefilesclone"></a>IDiaEnumSourceFiles::Clone
Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Clone ( 
   IDiaEnumSourceFiles** ppenum
);
```

#### <a name="parameters"></a>Параметры
 ppenum

[out] Возвращает [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) , содержащий копию перечислителя. Источник, который файлы не дублируются, только перечислитель.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)