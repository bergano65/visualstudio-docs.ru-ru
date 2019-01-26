---
title: IDebugProgram2::GetDebugProperty | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 359dd06c6105741ec2f7eec6428cbb2dc838f491
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951236"
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
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Свойства, возвращаемые этим методом относятся только к программе. Если программе необходимо вернуть более одного свойства, то [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объекта, возвращаемого этим методом является контейнером дополнительных свойств и вызова метода [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) возвращает метод список всех свойств.  
  
 Программы могут предоставлять любое количество и тип дополнительных свойств, которые могут быть описаны до `IDebugProperty2` интерфейс. Интегрированная среда разработки может отображать свойства дополнительные программы через пользовательский интерфейс браузера универсальное свойство.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)