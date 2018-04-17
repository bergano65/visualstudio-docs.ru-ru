---
title: IDebugProcessEx2::AddImplicitProgramNodes | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22f6cadaa88d6cc87ec70451d9da850cd49b7753
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
#### <a name="parameters"></a>Параметры  
 `guidLaunchingEngine`  
 [in] `GUID` Из Развернутой, будет использоваться для запуска программы (и предполагается, что добавлять свои собственные программы узлы).  
  
 `rgguidSpecificEngines`  
 [in] Массив `GUID`s DEs для программы будут добавлены узлы.  
  
 `celtSpecificEngines`  
 [in] Число `GUID`s в `rgguidSpecificEngines` массива.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [Программы узлы](../../../extensibility/debugger/program-nodes.md) будут добавлены для каждого DE, перечисленных в `rgguidSpecificEngines`— исключение при запуске подсистемы (как в `guidLaunchingEngine`), которой предполагается добавить собственный узел в программу, когда он запускает программу.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Узлы программы](../../../extensibility/debugger/program-nodes.md)