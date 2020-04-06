---
title: IDebugField::GetExtendedInfo Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc414dd57e86149e38d7c85d11252eb93efced51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728874"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Этот метод получает расширенную информацию о поле.

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
(в) Выбирает информацию, подаваемую. Допустимые значения:

|Значение|Описание|
|-----------|-----------------|
|`guidConstantValue`|Значение как последовательность байтов.|
|`guidConstantType`|Тип как подпись типа.|

`prgBuffer`\
(ваут) Возвращает расширенную информацию.

`pdwLen`\
(в, вне) Возвращает размер расширенной информации, в байтах.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 В настоящее время этот метод возвращает только тип или значение константы. Вызывающий абонент должен освободить `prgBuffer` буфер, возвращенный, позвонив `CoTaskMemFree` <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> в функцию COM (СЗ) или (СЗ).

## <a name="see-also"></a>См. также
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
