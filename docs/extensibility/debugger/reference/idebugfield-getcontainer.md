---
title: IDebugField::GetContainer | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugField::GetContainer
helpviewer_keywords:
- IDebugField::GetContainer method
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: de664eb2a5c53317da9732101187965e6e5c7509
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945838"
---
# <a name="idebugfieldgetcontainer"></a>IDebugField::GetContainer
Этот метод возвращает контейнер поля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetContainer(   
   IDebugContainerField** ppContainerField  
);  
```  
  
```csharp  
int GetContainer(  
   out IDebugContainerField ppContainerField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppContainerField`  
 [out] Возвращает контейнер, представленные как [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если это поле не имеет контейнер, возвращенный `ppContainerField` будет иметь значение null.  
  
## <a name="see-also"></a>См. также  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)