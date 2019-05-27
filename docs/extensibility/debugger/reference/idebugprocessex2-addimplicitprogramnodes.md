---
title: IDebugProcessEx2::AddImplicitProgramNodes | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 411b0b40d6c47f240472c82f727d955dda8df2df
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204083"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Этот метод добавляет узел программы для каждого ядра отладки (DE) указан.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT AddImplicitProgramNodes(
   REFGUID guidLaunchingEngine,
   GUID*   rgguidSpecificEngines,
   DWORD   celtSpecificEngines
);
```

```csharp
int AddImplicitProgramNodes(
   ref Guid guidLaunchingEngine,
   Guid[]   rgguidSpecificEngines,
   uint     celtSpecificEngines
);
```

## <a name="parameters"></a>Параметры
`guidLaunchingEngine`\
[in] `GUID` Из Развернутой, будет использоваться для запуска программ (и предполагается, что добавлять свои собственные узлы программы).

`rgguidSpecificEngines`\
[in] Массив `GUID`s из DEs, какие программы будут добавлены узлы.

`celtSpecificEngines`\
[in] Число `GUID`s в `rgguidSpecificEngines` массива.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
- [Программы узлы](../../../extensibility/debugger/program-nodes.md) добавляется для каждого DE, перечисленных в `rgguidSpecificEngines`— за исключением запуска ядра (как в `guidLaunchingEngine`), который предполагается добавить собственный узел программы при запуске программы.

## <a name="see-also"></a>См. также
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Узлы программы](../../../extensibility/debugger/program-nodes.md)