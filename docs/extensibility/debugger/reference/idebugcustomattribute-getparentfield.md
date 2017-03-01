---
title: "IDebugCustomAttribute::GetParentField | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 81ef2f6d125720ff7df30429395dc8a3b4d2f0cd
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Возвращает поле, к которому подключен пользовательский атрибут.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetParentField(   
   IDebugField** ppField  
);  
```  
  
```c#  
int GetParentField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppField`  
 [out] Возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объект, представляющий поле, к которому подключен пользовательский атрибут.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Вызов [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) метод для возвращенного [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) — объект, чтобы определить, что тип поля родительского.  
  
## <a name="see-also"></a>См. также  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
