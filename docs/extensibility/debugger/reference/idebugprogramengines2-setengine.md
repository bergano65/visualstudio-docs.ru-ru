---
title: IDebugProgramEngines2::SetEngine | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78755a75582ed3e61784b8e7762f7f9f6390a34c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697459"
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

#### <a name="parameters"></a>Параметры
 `guidEngine`

 [in] Идентификатор GUID DE.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)