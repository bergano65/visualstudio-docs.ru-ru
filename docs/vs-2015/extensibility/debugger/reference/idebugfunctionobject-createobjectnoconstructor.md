---
title: 'Идебугфунктионобжект:: Креатеобжектноконструктор | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ea00035eb220ccd08590ceaea6db98944f4657a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179458"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает объект без конструктора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT CreateObjectNoConstructor(   
   IDebugField*   pClassObject,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateObjectNoConstructor(  
   IDebugField      pClassField,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pClassObject`  
 окне Объект [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий тип создаваемого объекта.  
  
 `ppObject`  
 заполняет Возвращает объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий только что созданный объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Вызовите этот метод, чтобы создать объект, представляющий экземпляр структуры или сложного типа (который не требует конструктора), который является параметром функции, представленной интерфейсом [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
 Если для параметра объекта требуется конструктор, вызовите метод [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) .  
  
## <a name="see-also"></a>См. также:  
 [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md)   
 [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
