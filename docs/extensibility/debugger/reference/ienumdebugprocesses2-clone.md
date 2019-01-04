---
title: IEnumDebugProcesses2::Clone | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugProcesses2::Clone
helpviewer_keywords:
- IEnumDebugProcesses2::Clone
ms.assetid: 3d4196d3-5a80-4f76-b8b2-f72e80c8d406
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7813ba6731837b3437ba467c0ea9a9510d317be1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937262"
---
# <a name="ienumdebugprocesses2clone"></a>IEnumDebugProcesses2::Clone
Возвращает копию текущего перечисления как отдельный объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Clone(  
   IEnumDebugProcesses2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugProcesses2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnum`  
 [out] Возвращает копию этого перечисления как отдельный объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Копия перечисления имеет то же состояние, что исходный во время вызова этого метода. Тем не менее копии и исходного состояния отделены и могут изменяться по отдельности.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)