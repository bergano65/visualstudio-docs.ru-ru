---
title: "IDebugSymbolProvider::GetNextAddress | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
caps.latest.revision: 8
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
ms.openlocfilehash: 7f16f03e7e61fb059fdea10986ca76cf26b77590
ms.lasthandoff: 02/22/2017

---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
Возвращает адрес отладки, следующий за адресом отладки данного метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetNextAddress(   
   IDebugAddress*  pAddress,  
   BOOL            fStatementOnly,  
   IDebugAddress** ppAddress  
);  
```  
  
```c#  
int GetNextAddress(   
   IDebugAddress     pAddress,  
   bool              fStatementOnly,  
   out IDebugAddress ppAddress  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pAddress`  
 [in] Получает адрес отладки.  
  
 `fStatementOnly`  
 [in] Если значение равно TRUE, ограничивает адреса отладки в одной инструкции.  
  
 `ppAddress`  
 [out] Возвращает адрес следующего отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимые `HRESULT`, обычно S_OK.  
  
## <a name="see-also"></a>См. также  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
