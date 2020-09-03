---
title: 'IDebugModuleLoadEvent2:: module | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726720"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Возвращает модуль, который загружается или выгружается.

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
заполняет Возвращает объект [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , представляющий загружаемый или выгружаемый модуль.

`pbstrDebugMessage`\
[вход, выход] Возвращает необязательное сообщение с описанием этого события. Если этот параметр имеет значение null, сообщение не запрашивается.

`pbLoad`\
[вход, выход] Ненулевое значение ( `TRUE` ), если модуль загружается, и нуль ( `FALSE` ), если модуль выгружается. Если этот параметр имеет значение null, состояние не запрашивается.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
