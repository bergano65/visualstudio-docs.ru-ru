---
title: "IDebugExpressionEvaluator2::SetCallback | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
caps.latest.revision: 11
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
ms.openlocfilehash: f5f4757e09cc87d8481ae6501f178227df812fdc
ms.lasthandoff: 02/22/2017

---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Включает средство оценки выражений (EE) для указания интерфейс обратного вызова, отладчик ядра (DE) будет использовать для чтения параметры метрик.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT SetCallback (  
   IDebugSettingsCallback2* pCallback  
);  
```  
  
```c#  
int SetCallback (  
   IDebugSettingsCallback2 pCallback  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pCallback`  
 [in] Интерфейс для настройки обратного вызова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод предоставляет интерфейс к диспетчеру сеанса отладки, вычислитель выражений можно использовать для чтения параметры метрик. Он полезен в удаленной отладки для чтения метрики на [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] компьютере.  
  
## <a name="example"></a>Пример  
 В следующих примерах показано, как реализовать этот метод для **CEE** объекта, который предоставляет [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) интерфейса.  
  
```cpp#  
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)  
{  
    // precondition  
    INVARIANT( this );  
  
    // function body  
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)  
    {  
        EEDomain::fSetCallback DomainVal =  
        {  
            in_pCallback  
        };  
  
        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);  
        ENSURE( bSuccess );  
    }  
  
    // postcondition  
    INVARIANT( this );  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
