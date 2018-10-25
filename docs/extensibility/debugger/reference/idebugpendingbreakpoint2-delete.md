---
title: IDebugPendingBreakpoint2::Delete | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::Delete
helpviewer_keywords:
- IDebugPendingBreakpoint2::Delete method
- Delete method
ms.assetid: 4cb5ed81-6f0c-41ce-a770-5adb6b4bf5d9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b5b6b91dd871582c78be62202f7355ca68ffbea
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822089"
---
# <a name="idebugpendingbreakpoint2delete"></a>IDebugPendingBreakpoint2::Delete
Удаляет этот ожидающая точка останова и все точки останова, привязанный из него.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Delete(   
   void   
);  
```  
  
```csharp  
int Delete();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_BP_DELETED` Если точка останова была удалена.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простого `CPendingBreakpoint` объект, реализующий [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) интерфейс.  
  
```cpp  
HRESULT CPendingBreakpoint::Delete(void)    
{    
   HRESULT hr;    
  
   // Verify that the pending breakpoint has not been deleted. If deleted,    
   // then return hr = E_BP_DELETED.    
   if (m_state.state != PBPS_DELETED)    
   {    
      // If the pending breakpoint has bound and has an associated bound   
      // breakpoint, delete and release the bound breakpoint and set the   
      // pointer to NULL.    
      if (m_pBoundBP)    
      {    
         m_pBoundBP->Delete();    
         m_pBoundBP->Release();    
         m_pBoundBP = NULL;    
      }    
      // If the pending breakpoint did not bind and has an associated   
      // error breakpoint, release the error breakpoint and set the   
      // pointer to NULL.   
      if (m_pErrorBP)    
      {    
         m_pErrorBP->Release();    
         m_pErrorBP = NULL;    
      }    
  
      // Set the PENDING_BP_STATE in the PENDING_BP_STATE_INFO structure   
      // to deleted.     
      m_state.state = PBPS_DELETED;    
   }    
   else    
   {    
      hr = E_BP_DELETED;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>См. также  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)