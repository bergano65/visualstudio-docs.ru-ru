---
title: 'IDebugObject2:: Жетбаккингфиелдфорпроперти | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5eadbed61638ff1442c4ed7033426e245abf930a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62536390"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает поле или переменную (если есть), которые могут быть резервными копиями свойства, представленного этим объектом.  
  
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
 заполняет Объект [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) , описывающий резервное поле.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Объект [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) представляет свойство класса управляемого кода, то есть метод с методом доступа get и/или Set. Для таких свойств обычно требуется, чтобы переменная содержала значение, управляемое свойством. Эта переменная называется резервным полем. Если для объекта нет резервного поля, убедитесь, что возвращено значение NULL: некоторые вызывающие объекты могут не обратить внимание на возвращаемое значение, но вместо этого будет проверять, было ли возвращено значение NULL в `ppObject` .  
  
## <a name="see-also"></a>См. также:  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
