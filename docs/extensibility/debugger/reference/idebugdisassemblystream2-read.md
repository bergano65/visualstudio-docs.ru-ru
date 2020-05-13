---
title: IDebugDisassemblyStream2::Читать Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a4f5c0250405c2e2a0314b52c4cbc64d749fc0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732092"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Читает инструкции, начиная с текущего положения в потоке разборки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Read( 
   DWORD                     dwInstructions,
   DISASSEMBLY_STREAM_FIELDS dwFields,
   DWORD*                    pdwInstructionsRead,
   DisassemblyData*          prgDisassembly
);
```

```csharp
int Read( 
   uint                           dwInstructions,
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,
   out uint                       pdwInstructionsRead,
   DisassemblyData[]              prgDisassembly
);
```

## <a name="parameters"></a>Параметры
`dwInstructions`\
(в) Количество инструкций по разбору. Это значение также является максимальной длиной массива. `prgDisassembly`

`dwFields`\
(в) Комбинация флагов из [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) перечисления, которые `prgDisassembly` указывают, какие поля должны быть заполнены.

`pdwInstructionsRead`\
(ваут) Возвращает количество инструкций, фактически разобранных.

`prgDisassembly`\
(ваут) Массив структур [DisassemblyData,](../../../extensibility/debugger/reference/disassemblydata.md) заполненный разобранным кодом, по одной структуре на разобранную инструкцию. Длина этого массива определяется `dwInstructions` параметром.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Максимальное количество инструкций, доступных в текущей области, можно получить, позвонив в метод [GetSize.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)

 Текущее положение, из которой читается следующая инструкция, может быть изменено, позвонив в метод [Seek.](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)

 Флаг `DSF_OPERANDS_SYMBOLS` может быть добавлен `DSF_OPERANDS` к `dwFields` флагу в параметре, чтобы указать, что имена символов должны использоваться при демонтаже инструкций.

## <a name="see-also"></a>См. также
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
