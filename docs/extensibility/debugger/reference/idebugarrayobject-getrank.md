---
title: IDebugArrayObject::GetRank | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 333dca88fae59d4407e6be813b2241d070648648
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923046"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Возвращает ранг массива, то есть число измерений.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwRank`  
 [out] Возвращает ранг.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Используйте [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) метод для извлечения размер каждого измерения массива объекта.  
  
## <a name="see-also"></a>См. также  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)