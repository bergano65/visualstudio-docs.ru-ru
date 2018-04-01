---
title: IDebugProgram2::GetDebugProperty | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2263b96f64a72e9c89061d1ca3b7792526a8231b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Возвращает свойства программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppProperty`  
 [out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий свойства программы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Свойства, возвращаемый этим методом относятся к программе. Необходим для возврата более одного свойства, то [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объект, возвращаемый этим методом является контейнером для дополнительных свойств и вызова [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) возвращает метод список всех свойств.  
  
 Программы могут предоставлять любое число и тип дополнительные свойства, которые могут быть описаны до `IDebugProperty2` интерфейса. Интегрированная среда разработки может отображаться свойства дополнительные программы через пользовательский интерфейс обозревателя универсальное свойство.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)