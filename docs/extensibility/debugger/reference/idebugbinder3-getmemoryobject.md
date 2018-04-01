---
title: IDebugBinder3::GetMemoryObject | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBinder3::GetMemoryObject
helpviewer_keywords:
- IDebugBinder3::GetMemoryObject method
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7375b49582faac47c6056777170bd1c710a28b22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinder3getmemoryobject"></a>IDebugBinder3::GetMemoryObject
Этот метод возвращает объект памяти, который представляет объем памяти, к которому привязан этот объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetMemoryObject(  
   IDebugField*   pField,  
   UINT64         uConstant,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int GetMemoryObject(  
   IDebugField      pField,  
   long             uConstant,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pField`  
 [in] Указывает, какое поле для получения для объекта памяти.  
  
 `uConstant`  
 [in] Представляет адрес памяти или значение для постоянного значения.  
  
 `ppObject`  
 [out] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) представляющий памяти, к которому привязан этот объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)