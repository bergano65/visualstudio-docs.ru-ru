---
title: IDebugEvent2::GetAttributes | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 117ca6867cef7f14de90213514a186662d1060b8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Получает атрибуты для этого события отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetAttribute(   
   DWORD* pdwAttrib  
);  
```  
  
```csharp  
int GetAttribute(   
   out uint pdwAttrib  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwAttrib`  
 [out] Сочетание флагов из [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) перечисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейса являются общими для всех событий. Этот метод описывается тип события; Например, события синхронным или асинхронным, и это событие остановки.  
  
## <a name="see-also"></a>См. также  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)