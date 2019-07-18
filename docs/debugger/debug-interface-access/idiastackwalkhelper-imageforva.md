---
title: IDiaStackWalkHelper::imageForVA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56f71364f28bec56c058a52f5a9e79c6bba298b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837957"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
Возвращает дату начала исполняемый образ в памяти, выделяемый виртуальный адрес где-то в область памяти.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT imageForVA(
   ULONGLONG  vaContext,
   ULONGLONG *pvaImageStart
);
```

#### <a name="parameters"></a>Параметры
 `vaContext`

[in] Виртуальный адрес, который лежит где-то в пространстве исполняемый файл.

 `pvaImageStart`

[out] Возвращает начальный виртуальный адрес исполняемого образа.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)