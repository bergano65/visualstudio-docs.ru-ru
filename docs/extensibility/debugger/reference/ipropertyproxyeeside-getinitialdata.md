---
title: "IPropertyProxyEESide::GetInitialData | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IPropertyProxyEESide::GetInitialData
helpviewer_keywords: IPropertyProxyEESide::GetInitialData
ms.assetid: 36cceb19-2604-4ef9-b42b-5dd30cbe24b1
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 978acc645444cb675d2d2fd912780dbb0ceac32a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ipropertyproxyeesidegetinitialdata"></a>IPropertyProxyEESide::GetInitialData
Возвращает исходные данные для этого объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetInitialData(  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int GetInitialData(  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dataOut`  
 [out] Возвращает [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) объект, содержащий начальные данные для этого объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)