---
title: IDiaStackWalkFrame::searchForReturnAddressStart | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddressStart method
ms.assetid: 47660b9b-6e4f-4dfa-88ab-63dce28f7412
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf7de77016f5ccc15f2cea8bf3172321dd824096
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640757"
---
# <a name="idiastackwalkframesearchforreturnaddressstart"></a>IDiaStackWalkFrame::searchForReturnAddressStart
Выполняет поиск указанного кадра стека для возврата адреса близка к указанному адресу.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT searchForReturnAddressStart ( 
   IDiaFrameData* frame,
   ULONGLONG      startAddress,
   ULONGLONG*     returnAddress
);
```

#### <a name="parameters"></a>Параметры
 `frame`

[in] [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , представляющий текущий кадр стека.

 `startAddress`

[in] Адрес виртуальной памяти, с которого начинается поиск.

 `returnAddress`

[out] Возвращает функцию ближайшего обратный адрес `startAddress`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)