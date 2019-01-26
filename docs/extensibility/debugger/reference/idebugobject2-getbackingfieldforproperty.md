---
title: IDebugObject2::GetBackingFieldForProperty | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c74b99c1ca4895cb5e930fa7f17ec21a5db61cff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954518"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Получает поле или переменная (если таковые имеются), может резервного свойства, представленного этим объектом.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppObject`  
 [out] [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) описывающий резервное поле.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) объект, представляющий свойство класса управляемого кода, то есть метод с помощью метода get и/или метода доступа set. Такие свойства обычно требуют переменной для хранения значения, обработанные свойства. Эта переменная называется резервное поле. Если нет резервного поля для объекта, затем убедитесь, что вернуть значение null: некоторые вызывающие объекты могут не обращайте внимания на возвращаемое значение, но вместо этого будет выглядеть для просмотра, если значение null был возвращен в `ppObject`.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)