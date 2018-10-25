---
title: IDebugObject2::GetBackingFieldForProperty | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d788d048fc428825cbc667b18424b32c68ddc5c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840237"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Получает поле или переменная (если таковые имеются), может резервного свойства, представленного этим объектом.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
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