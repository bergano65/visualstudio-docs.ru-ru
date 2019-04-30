---
title: IDiaStackWalkFrame::put_registerValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::put_registerValue method
ms.assetid: 2d8b79b6-7240-43fe-b24e-e4ff3e2c15b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 440c7d19382b813b3f34451d7c177c6e8b57f16f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831851"
---
# <a name="idiastackwalkframeputregistervalue"></a>IDiaStackWalkFrame::put_registerValue
Задает значение регистра.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT put_registerValue ( 
   DWORD     index,
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Параметры
 `index`

[in] Значение из [перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) перечисление, определяющее, зарегистрируйтесь для записи.

 `NewVal`

[in] Новое значение регистра.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [Перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)