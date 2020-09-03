---
title: 'Идебугфунктионобжект:: Evaluate | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e19baa193bb015056b9e5abde4c7a274f635c0c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179422"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Вызывает функцию и возвращает результирующее значение в виде объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppParams`  
 окне Массив объектов [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющих входные параметры. Каждый из этих параметров был создан с помощью одного из `Create` методов в интерфейсе [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
 `dwParams`  
 окне Число параметров в `ppParams` массиве.  
  
 `dwTimeout`  
 окне Указывает максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте `INFINITE` для бесконечного ожидания.  
  
 `ppResult`  
 заполняет Возвращает [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий значение функции в виде объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод настраивает и выполняет вызов функции, представленной объектом [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
