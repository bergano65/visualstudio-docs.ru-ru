---
title: IDiaStackFrame::get_lengthParams | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_lengthParams method
ms.assetid: 78005efa-2883-4823-b4e4-711a66672c78
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8505556e814493078bcd3944768011a2405510c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630578"
---
# <a name="idiastackframegetlengthparams"></a>IDiaStackFrame::get_lengthParams
Возвращает число байтов параметров в стек.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_lengthParams ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает число байтов параметров.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)