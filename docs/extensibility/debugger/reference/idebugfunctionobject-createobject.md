---
title: IDebugFunctionObject::CreateObject | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b0b9a36dfac48d86963db68c3ab68500d8b8bfba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Создает объект, с помощью конструктора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pConstructor`  
 [in] [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) объект, представляющий конструктор создаваемого объекта.  
  
 `dwArgs`  
 [in] Число параметров в `pArg` массива. Представляет число параметров, переданный в конструктор.  
  
 `pArg`  
 [in] Массив [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объектов, представляющих параметры, передаваемые конструктору.  
  
 `ppObject`  
 [out] Возвращает `IDebugObject` представляет вновь созданный объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается для создания объекта, который представляет экземпляр класса (или другие сложный тип, который требуется конструктор), параметр функции, который представляется [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейса.  
  
 Если объект параметра не требуется конструктор, вызовите [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)