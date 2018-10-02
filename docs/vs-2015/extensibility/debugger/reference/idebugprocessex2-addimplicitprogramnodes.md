---
title: IDebugProcessEx2::AddImplicitProgramNodes | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
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
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2552731cf9150e4e86a7ef4bf6d927aaac33cc7a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568799"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProcessEx2::AddImplicitProgramNodes](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes).  
  
Этот метод добавляет узел программы для каждого ядра отладки (DE) указан.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [in] `GUID` Из Развернутой, будет использоваться для запуска программ (и предполагается, что добавлять свои собственные узлы программы).  
  
 `rgguidSpecificEngines`  
 [in] Массив `GUID`s из DEs, какие программы будут добавлены узлы.  
  
 `celtSpecificEngines`  
 [in] Число `GUID`s в `rgguidSpecificEngines` массива.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [Программы узлы](../../../extensibility/debugger/program-nodes.md) добавляется для каждого DE, перечисленных в `rgguidSpecificEngines`— за исключением запуска ядра (как в `guidLaunchingEngine`), который предполагается добавить собственный узел программы при запуске программы.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Узлы программы](../../../extensibility/debugger/program-nodes.md)

