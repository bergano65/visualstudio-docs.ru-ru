---
title: "IDebugSymbolProvider::GetAddressesFromPosition | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
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
ms.openlocfilehash: 28c913ca924274c946b3ce52a964a3efbae6dc5c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Этот метод сопоставляет позицию документа в массив адресов отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetAddressesFromPosition(   
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```c#  
int GetAddressesFromPosition(   
   IDebugDocumentPosition2  pDocPos,  
   bool                     fStatmentOnly,  
   out IEnumDebugAddresses  ppEnumBegAddresses,  
   out IEnumDebugAddresses  ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pDocPos`  
 [in] Позиция документа.  
  
 `fStatmentOnly`  
 [in] Если значение равно TRUE, ограничивает адреса отладки в одной инструкции.  
  
 `ppEnumBegAddresses`  
 [out] Возвращает перечислитель для начала отладки адресов, связанных с этой инструкции или строке.  
  
 `ppEnumEndAddresses`  
 [out] Возвращает [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) перечислитель для конечного адреса отладки, связанные с этой инструкции или строке.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Позиция документа обычно указывает диапазон строк исходного кода. Этот метод предоставляет начальный и конечный адреса отладки связанных с этими строками. В некоторых языках разрешить с помощью инструкций, охватывающих несколько строк или строк, содержащих более одной инструкции. Этот метод обеспечивает флаг для ограничения отладки адреса в одной инструкции.  
  
 Можно иметь несколько адресов отладки, как и в случае шаблоны одного оператора.  
  
## <a name="see-also"></a>См. также  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
