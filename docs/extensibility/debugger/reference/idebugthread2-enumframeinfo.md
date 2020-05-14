---
title: IDebugThread2::EnumFrameInfo Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bd3c6d46a577930cc7a2b87c85cd82a55f8cf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718859"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Извлекает список кадров стека для этого потока.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumFrameInfo ( 
   FRAMEINFO_FLAGS        dwFieldSpec,
   UINT                   nRadix,
   IEnumDebugFrameInfo2** ppEnum
);
```

```csharp
int EnumFrameInfo ( 
   enum_FRAMEINFO_FLAGS     dwFieldSpec,
   uint                     nRadix,
   out IEnumDebugFrameInfo2 ppEnum
);
```

## <a name="parameters"></a>Параметры
`dwFieldSpec`\
(в) Комбинация флагов [из FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) перечисления, которая определяет, какие поля структур [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) должны быть заполнены. Укажите `FIF_FUNCNAME_FORMAT` флаг для формата имени функции в одну строку.

`nRadix`\
(в) Radix используется при форматировании численной информации в регистраторе.

`ppEnum`\
(ваут) Возвращает объект [IEnumDebugFrameInfo2,](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) содержащий список структур [FRAMEINFO,](../../../extensibility/debugger/reference/frameinfo.md) описывающих кадр стека.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Кадры потока перечислены в порядке, с текущей кадра перечислены первый и старейший кадр перечислены в прошлом.

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
