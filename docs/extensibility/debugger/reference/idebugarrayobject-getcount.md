---
title: IDebugArrayObject::GetCount | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0058599a6f7967aa96490223de519b69710242ea
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023006"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Получает число элементов в массиве.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwElements`  
 [out] Возвращает число.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод видит все элементы объекта массива как одномерный массив, даже если объект массива имеет несколько измерений. Например, если имеется массив `myarray[3][2][6]`, этот метод возвращал 36 в `pdwElements` параметра. Используйте [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) метод для извлечения отдельных элементов одной за раз.  
  
## <a name="see-also"></a>См. также  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)