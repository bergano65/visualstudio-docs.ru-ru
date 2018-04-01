---
title: IDebugProcessEx2::AddImplicitProgramNodes | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: adc3f54188e57bd5453703c0aa68fe281fd2ca5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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