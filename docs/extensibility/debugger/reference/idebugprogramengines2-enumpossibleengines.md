---
title: IDebugProgramEngines2::EnumPossibleEngines Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45916edbef4368c58f83426d6c73f3c692236cb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722432"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Возвращает GUID для всех возможных отладок двигателей (DE), которые могут отладить эту программу.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumPossibleEngines( 
   DWORD  celtBuffer,
   GUID*  rgguidEngines,
   DWORD* pceltEngines
);
```

```csharp
int EnumPossibleEngines( 
   uint      celtBuffer,
   GUID[]    rgguidEngines,
   ref DWORD pceltEngines
);
```

## <a name="parameters"></a>Параметры
`celtBuffer`\
(в) Количество DE GUIDs, чтобы вернуться. Это также определяет максимальный размер `rgguidEngines` массива.

`rgguidEngines`\
(в, вне) Массив DE GUIDs, которые должны быть заполнены.

`pceltEngines`\
(ваут) Возвращает фактическое количество возвратимых DE GUID.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает (C) `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` или «C» 0x8007007A, если буфер недостаточно велик.

## <a name="remarks"></a>Примечания
 Для того, чтобы определить, сколько двигателей, `celtBuffer` позвоните по этому `rgguidEngines` методу один раз с параметром, установленным до 0, и параметром, установленным на нулевую величину. Это `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` возвращает (0x8007007A для C), и `pceltEngines` параметр возвращает необходимый размер буфера.

## <a name="see-also"></a>См. также
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
