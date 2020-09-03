---
title: IDebugStackFrame2::/info | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetInfo
helpviewer_keywords:
- IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 09768fc58640d79a3b5628bafc16b2267f1f8a4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719722"
---
# <a name="idebugstackframe2getinfo"></a>IDebugStackFrame2::GetInfo
Возвращает описание кадра стека.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetInfo ( 
   FRAMEINFO_FLAGS dwFieldSpec,
   UINT            nRadix,
   FRAMEINFO*      pFrameInfo
);
```

```csharp
int GetInfo ( 
   enum_FRAMEINFO_FLAGS dwFieldSpec,
   uint                 nRadix,
   FRAMEINFO[]          pFrameInfo
);
```

## <a name="parameters"></a>Параметры
`dwFieldSpec`\
окне Сочетание флагов из перечисления [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) , которое указывает, какие поля параметра должны `pFrameInfo` быть заполнены.

`nRadix`\
окне Основание системы счисления, используемое при форматировании любой числовой информации.

`pFrameInfo`\
заполняет Структура [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) , которая заполняется описанием кадра стека.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
