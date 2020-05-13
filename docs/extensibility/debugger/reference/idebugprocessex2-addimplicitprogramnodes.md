---
title: IDebugProcessEx2:AddImplicitProgramNodes Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 113c81e95e7384be04b7e02a5c58cd2cad7c9c6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723392"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Этот метод добавляет узлы программы для каждого указанного движка отладки (DE).

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
(в) DE, `GUID` который будет использоваться для запуска программ (и предполагается добавить свои собственные узлы программы).

`rgguidSpecificEngines`\
(в) Массив `GUID`s DEs, для которых будут добавлены узлы программы.

`celtSpecificEngines`\
(в) Количество `GUID`s в `rgguidSpecificEngines` массиве.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
- [Узлы программы](../../../extensibility/debugger/program-nodes.md) будут добавлены для `rgguidSpecificEngines`каждого DE, перечисленных `guidLaunchingEngine`в - за исключением запускающего двигателя (как указано в ), который предполагается добавить свой собственный узлы программы, когда он запускает программу.

## <a name="see-also"></a>См. также
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Узлы программы](../../../extensibility/debugger/program-nodes.md)
