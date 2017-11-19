---
title: "IDebugClassField::EnumNestedEnums | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::EnumNestedEnums
helpviewer_keywords: IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7667e21f57f3fc2844800e498d9519ddf9929f85
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Создает перечислитель для вложенных перечислителей этого класса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnum`  
 [out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список вложенных перечислений. Возвращает значение null, если нет вложенных перечислений.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK, или возвращает значение S_FALSE, если нет вложенной перечислителей. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Каждый элемент перечисления является [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) объект, описывающий вложенных перечисления.  
  
 Перечисление, объявленное в классе считается вложенных перечисления. Например, если учитывать, что:  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 `EnumNestedEnums` Метод вернет [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, который содержит один [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) , представляющий `NestedEnum` перечисления.  
  
## <a name="see-also"></a>См. также  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)