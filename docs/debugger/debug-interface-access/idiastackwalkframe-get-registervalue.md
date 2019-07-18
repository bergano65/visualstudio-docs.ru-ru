---
title: IDiaStackWalkFrame::get_registerValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::get_registerValue method
ms.assetid: ca3c20a9-934a-4b2c-a7f6-7d06e8611ff2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d60fa2ebefb7e1e4eefccce866a1059fdbc78a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837983"
---
# <a name="idiastackwalkframegetregistervalue"></a>IDiaStackWalkFrame::get_registerValue
Получает значение регистра.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `index`

[in] Значение из [перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) перечисление, определяющее, зарегистрируйтесь, чтобы получить значение.

 `pRetVal`

[out] Возвращает текущее значение регистра.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [Перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)