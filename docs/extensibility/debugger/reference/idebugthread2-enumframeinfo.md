---
title: IDebugThread2::EnumFrameInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fad77ca1d649e7ffdda02c7145dc11666619f232
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320323"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Извлекает список кадров стека для данного потока.

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
[in] Сочетание флагов из [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) перечисления, указывающее, какие поля [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры являются для заполнения. Укажите `FIF_FUNCNAME_FORMAT` флаг формата имени функции в одну строку.

`nRadix`\
[in] Основание системы счисления, используемый для форматирования числовые данные в перечислителе.

`ppEnum`\
[out] Возвращает [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) , содержащий список [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структур, описывающих кадр стека.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Кадры потока перечисляются в порядке, с текущего кадра, перечислению в первую и старый, последнего перечисления.

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)