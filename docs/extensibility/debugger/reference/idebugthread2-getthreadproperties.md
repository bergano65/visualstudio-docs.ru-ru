---
title: "IDebugThread2::GetThreadProperties | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::GetThreadProperties
helpviewer_keywords: IDebugThread2::GetThreadProperties
ms.assetid: 304403fd-f4f8-4096-ac2c-bd3b59663aad
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8fb7b3979550570285b2542f8c9fe35d8d54306d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugthread2getthreadproperties"></a>IDebugThread2::GetThreadProperties
Возвращает свойства, описывающие этот поток.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetThreadProperties (   
   THREADPROPERTY_FIELDS dwFields,  
   THREADPROPERTIES*     ptp  
);  
```  
  
```csharp  
int GetThreadProperties (   
   enum_THREADPROPERTY_FIELDS dwFields,  
   THREADPROPERTIES[]         ptp  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFields`  
 [in] Сочетание флагов из [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) перечисления, которое определяет, какие поля `ptp` должны быть заполнены.  
  
 `ptp`  
 [in, out] Объект [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) структуры, который содержит свойства потока.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Сведения, возвращаемые этим методом, обычно указывается в **потоков** окон отладки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простой `CProgram` объект, реализующий [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) интерфейса.  
  
```cpp  
HRESULT CProgram::GetThreadProperties(THREADPROPERTY_FIELDS dwFields,  
                                      THREADPROPERTIES *ptp)  
{  
    HRESULT hr = E_FAIL;    
  
    // Check for valid argument.    
   if (ptp)    
    {    
      // Create an array of buffers at ptp the size of the  
      // THREADPROPERTIES structure and set all of the  
      // buffers at ptp to 0.    
      memset(ptp, 0, sizeof (THREADPROPERTIES));    
  
      // Check if there is a valid THREADPROPERTY_FIELDS and the TPF_ID flag is set.    
      if (dwFields & TPF_ID)    
      {    
         // Check for successful assignment of the current thread ID to  
         //  the dwThreadId of the passed THREADPROPERTIES.    
         if (GetThreadId(&(ptp->dwThreadId)) == S_OK)    
         {    
            // Set the TPF_ID flag in the THREADPROPERTY_FIELDS enumerator    
            // of the passed THREADPROPERTIES.    
            ptp->dwFields |= TPF_ID;    
         }    
      }    
  
      hr = S_OK;    
    }    
    else    
        hr = E_INVALIDARG;    
  
    return hr;    
}    
```  
  
## <a name="see-also"></a>См. также  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)