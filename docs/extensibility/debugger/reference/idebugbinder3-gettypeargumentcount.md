---
title: "IDebugBinder3::GetTypeArgumentCount | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::GetTypeArgumentCount
helpviewer_keywords: IDebugBinder3::GetTypeArgumentCount method
ms.assetid: caf68de6-6f7c-4efd-b803-121347a5032e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b6db87ba6ebb2dbe9e6bcd70ffc691e3c3857c1a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbinder3gettypeargumentcount"></a>IDebugBinder3::GetTypeArgumentCount
Этот метод возвращает количество типов аргументов, связанный с данным объектом.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetTypeArgumentCount(  
   UINT* uCount  
);  
```  
  
```csharp  
int GetTypeArgumentCount(  
   out uint uCount  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `uCount`  
 [out] Количество типов аргументов, связанный с данным объектом.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Значение, возвращенное этим методом может использоваться для выделения массив для использования с [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)