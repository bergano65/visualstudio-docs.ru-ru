---
title: 'IDebugProcess2:: Port | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetPort
helpviewer_keywords:
- IDebugProcess2::GetPort
ms.assetid: e39b6e5a-64eb-48cf-a53d-da4fdb968e2d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1cfc4c4e0f12400ff0fe07b24acaed0b80039f94
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907844"
---
# <a name="idebugprocess2getport"></a>IDebugProcess2::GetPort
Возвращает порт, на котором выполняется процесс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPort( 
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>Параметры
`ppPort`\
заполняет Возвращает объект [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , представляющий порт, в котором был запущен процесс.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
