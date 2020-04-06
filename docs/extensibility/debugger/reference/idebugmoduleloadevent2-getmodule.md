---
title: IDebugModuleLoadEvent2:GetModule Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b90547709e5524ce005b0598b0b8d482cfecf173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726720"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Получает модуль, который загружается или выгружается.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

## <a name="parameters"></a>Параметры
`pModule`\
(ваут) Возвращает объект [IDebugModule2,](../../../extensibility/debugger/reference/idebugmodule2.md) представляющий модуль, который загружается или разгружается.

`pbstrDebugMessage`\
(в, вне) Возвращает дополнительное сообщение, описывающее это событие. Если этот параметр является нулевая величина, сообщение не запрашивается.

`pbLoad`\
(в, вне) Nonzero`TRUE`( ), если модуль загружается и ноль ( ),`FALSE`если модуль разгрузки. Если этот параметр является нулевая величина, статус не запрашивается.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
