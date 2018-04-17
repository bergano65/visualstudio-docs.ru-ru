---
title: IDebugMethodField::EnumStaticLocals | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 761e696cd774e0414b58c9d2a9f1482d298489f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Создает перечислитель для статических локальных переменных метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppLocals`  
 [out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список статических локальных переменных. Возвращает значение null, если нет статических локальных переменных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK, или возвращает значение S_FALSE, если нет статических локальных переменных. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Каждый элемент является [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объектов, представляющих различные типы статических локальных переменных. Вызовите [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) метод для каждого объекта, чтобы определить точно локального статического объекта вида.  
  
## <a name="see-also"></a>См. также  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)