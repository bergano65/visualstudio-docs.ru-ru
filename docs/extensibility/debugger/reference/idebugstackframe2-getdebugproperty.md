---
title: IDebugStackFrame2::GetDebugProperty | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetDebugProperty
helpviewer_keywords:
- IDebugStackFrame2::GetDebugProperty
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d0fcb648f25667d47a164c14443bafd14cc315f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2getdebugproperty"></a>IDebugStackFrame2::GetDebugProperty
Возвращает описание свойств кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetDebugProperty (   
   IDebugProperty2** ppDebugProp  
);  
```  
  
```csharp  
int GetDebugProperty (   
   out IDebugProperty2 ppDebugProp  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppDebugProp`  
 [out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объект, описывающий свойства данного кадра стека.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Вызов [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) можно извлечь метод с подходящими фильтрами локальных переменных, параметров методов, регистры и указатель «this», связанный с этим кадром стека.  
  
## <a name="see-also"></a>См. также  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)