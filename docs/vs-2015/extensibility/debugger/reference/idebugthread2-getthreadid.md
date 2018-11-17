---
title: IDebugThread2::GetThreadId | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 913a83325b527dc65484b535549ec791e3a09138
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772538"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает идентификатор потока системы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Идентификатор потока используется для идентификации потока используется всеми потоками процесса.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простого `CProgram` объект, реализующий [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) интерфейс.  
  
```cpp#  
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {     
   *pdwThreadId = GetCurrentThreadId();    
   return NOERROR;    
}    
```  
  
## <a name="see-also"></a>См. также  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)

