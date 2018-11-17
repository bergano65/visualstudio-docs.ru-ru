---
title: IDebugObject2::GetBackingFieldForProperty | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 750a881fe6a73ef1bf43f928c8aa11d9b6a5643a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752303"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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

