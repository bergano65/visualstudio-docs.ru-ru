---
title: "IDebugObject::SetValue | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::SetValue
helpviewer_keywords: IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e4a4311d5e115e20d23096a6ca1e3bce2dcbea6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Задает значение объекта из последовательных последовательность байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int SetValue(  
   byte[] pValue,   
   uint   nSize  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pValue`  
 [in] Массив байтов, представляющий новое значение.  
  
 `nSize`  
 [in] Размер значения в байтах.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Значения в массиве копируются в это [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объекта, заменяют существующее значение. Размер нового значения может быть больше или меньше существующее значение. Это `IDebugObject` не может быть пустой ссылкой.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)