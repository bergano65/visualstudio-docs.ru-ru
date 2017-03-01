---
title: "IDebugCodeContext3::GetModule | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugCodeContext3::GetModule
ms.assetid: 8e4317b8-8255-486c-a896-a68ed94f8aa1
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c45688d1238e961a68166e199d696cfa98f6b536
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcodecontext3getmodule"></a>IDebugCodeContext3::GetModule
Извлекает ссылку на интерфейс модуля отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetModule(   
   IDebugModule2 **ppModule  
);  
```  
  
```c#  
public int GetModule(   
   out IDebugModule2 ppModule  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppModule`  
 [out] Ссылка на интерфейс модуля отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для **CDebugCodeContext** объекта, который предоставляет [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) интерфейса.  
  
```cpp#  
HRESULT CDebugCodeContext::GetModule(IDebugModule2** ppModule)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
  
    IfFalseGo( ppModule, E_INVALIDARG );  
    *ppModule = NULL;  
  
    IfFailGo( this->GetModule(&pModule) );  
    IfFailGo( pModule->QueryInterface(IID_IDebugModule2, (void**) ppModule) );  
  
Error:  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)
