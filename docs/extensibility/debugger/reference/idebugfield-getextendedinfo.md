---
title: IDebugField::GetExtendedInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3ddae4ea7ecc58d67279ae638d19bf95ec2cc591
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352654"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Этот метод возвращает расширенные сведения о поле.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetExtendedInfo( 
   REFGUID guidExtendedInfo,
   BYTE**  prgBuffer,
   DWORD*  pdwLen
);
```

```csharp
int GetExtendedInfo(
   ref Guid guidExtendedInfo,
   IntPtr[] prgBuffer,
   ref uint pdwLen
);
```

## <a name="parameters"></a>Параметры
`guidExtendedInfo`\
[in] Выбирает возвращаемые данные. Допустимые значения:

|Значение|Описание|
|-----------|-----------------|
|`guidConstantValue`|Значение в виде последовательности байтов.|
|`guidConstantType`|Тип в виде сигнатура типа.|

`prgBuffer`\
[out] Возвращает расширенные сведения.

`pdwLen`\
[in, out] Возвращает размер расширенных сведений, в байтах.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 В настоящее время этот метод возвращает только типа или значения константы. Вызывающий объект должен освободить буфер, возвращается в `prgBuffer` путем вызова COM `CoTaskMemFree` функции (C++) или <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).

## <a name="see-also"></a>См. также
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)