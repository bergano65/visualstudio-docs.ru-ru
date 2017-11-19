---
title: "IDebugThread2::GetThreadId | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::GetThreadId
helpviewer_keywords: IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 19879a3e87d1d2ca986cdff36d9389cac43394ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
Получает идентификатор потока системы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetThreadId (   
   DWORD* pdwThreadId  
);  
```  
  
```csharp  
int GetThreadId (   
   out uint pdwThreadId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwThreadId`  
 [out] Возвращает идентификатор потока системы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Идентификатор потока используется для идентификации потока используются всеми потоками процесса.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простой `CProgram` объект, реализующий [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) интерфейса.  
  
```cpp  
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {     
   *pdwThreadId = GetCurrentThreadId();    
   return NOERROR;    
}    
```  
  
## <a name="see-also"></a>См. также  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)