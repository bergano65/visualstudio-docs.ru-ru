---
title: IDebugProcess3::DisableENC Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b39bb448501bacd5ab458b7e61bb1a5044bc8a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723730"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Этот метод явно отстраняет от Edit и Продолжить этот процесс (и все программы, которые он содержит). Поставщик пользовательских портов `E_NOTIMPL`должен всегда возвращаться.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Параметры
`reason`\
(в) Значение из [encUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) перечисления.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки.

> [!NOTE]
> Поставщик пользовательских портов `E_NOTIMPL`должен всегда возвращаться.

## <a name="remarks"></a>Примечания
 После того, как edit and Continue отключен для процесса, он может быть восстановлен только путем перезапуска процесса.

## <a name="see-also"></a>См. также
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
