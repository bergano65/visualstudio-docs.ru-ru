---
title: 'IDebugProcessEx2:: АддимплиЦитпрограмнодес | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: faca728144bde572d8a1d3424fbfcf908403d679
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202817"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод добавляет узел программы для каждого указанного модуля отладки (DE).  
  
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
 окне Параметр `GUID` de, который используется для запуска программ (предполагает добавление собственных узлов программы).  
  
 `rgguidSpecificEngines`  
 окне Массив типа `GUID` DEs, для которого будут добавлены узлы программ.  
  
 `celtSpecificEngines`  
 окне Число элементов `GUID` в `rgguidSpecificEngines` массиве.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 [Узлы программы](../../../extensibility/debugger/program-nodes.md) будут добавляться для каждого из них, кроме `rgguidSpecificEngines` модуля запуска (как указано в `guidLaunchingEngine` ), который предполагает добавление собственного узла программы при запуске программы.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Узлы программы](../../../extensibility/debugger/program-nodes.md)
