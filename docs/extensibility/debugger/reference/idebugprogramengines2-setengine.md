---
title: IDebugProgramEngines2::SetEngine | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1a8c48de1a068300bb514d10528592cc518004db
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343450"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
Подсистема обработки программа или программа узел какие отладки (DE), чтобы использовать для отладки этой программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetEngine( 
   REFGUID guidEngine
);
```

```csharp
int SetEngine( 
   ref Guid guidEngine
);
```

## <a name="parameters"></a>Параметры
`guidEngine`\
[in] Идентификатор GUID DE.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)