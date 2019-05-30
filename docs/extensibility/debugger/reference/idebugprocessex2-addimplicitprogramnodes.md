---
title: IDebugProcessEx2::AddImplicitProgramNodes | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b75ef50107b44de8de6f65c5c4c9c6827e13426e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309489"
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