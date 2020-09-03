---
title: 'Идебугфунктионобжект:: CreateObject | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08483d5f015af7088eb5968a5bf6358ce5065579
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179475"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает объект с помощью конструктора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Объект [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) , представляющий конструктор создаваемого объекта.  
  
 `dwArgs`  
 окне Число параметров в `pArg` массиве. Представляет число параметров, передаваемых конструктору.  
  
 `pArg`  
 окне Массив объектов [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющих параметры, передаваемые конструктору.  
  
 `ppObject`  
 заполняет Возвращает объект, `IDebugObject` представляющий созданный объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Вызовите этот метод, чтобы создать объект, представляющий экземпляр класса (или другого сложного типа, которому требуется конструктор), который является параметром функции, представленной интерфейсом [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
 Если параметру объекта не требуется конструктор, вызовите метод [креатеобжектноконструктор](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) .  
  
## <a name="see-also"></a>См. также:  
 [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
