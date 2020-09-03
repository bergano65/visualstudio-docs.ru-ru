---
title: 'Идебугобжект:: Сетреференцевалуе | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b1da0e152d536e9bed47dfb3964df60634c017bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180501"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Задает значение ссылки для этого объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT SetReferenceValue(   
   IDebugObject* pObject  
);  
```  
  
```csharp  
int SetReferenceValue(  
   [In] IDebugObject pObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pObject`  
 окне Объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий новое значение ссылки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод делает этот объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) ссылкой на значение объекта, указанного в `pObject` параметре, вызывая предыдущую ссылку. Обратите внимание, что этот `IDebugObject` объект уже должен быть ссылочным типом.  
  
## <a name="see-also"></a>См. также:  
 [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
