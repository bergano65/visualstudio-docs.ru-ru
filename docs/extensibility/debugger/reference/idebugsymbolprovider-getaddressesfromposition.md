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
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dd01516386d68d3a17d56061f7fcd27109212b6b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Этот метод сопоставляет позицию документа в массив адресов отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetAddressesFromPosition(   
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```csharp  
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
 [in] Если значение равно TRUE, ограничивает отладки адреса для одной инструкции.  
  
 `ppEnumBegAddresses`  
 [out] Возвращает перечислитель для начала отладки адреса, связанные с этой инструкции или строке.  
  
 `ppEnumEndAddresses`  
 [out] Возвращает [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) перечислитель для конечного адреса отладки, связанные с этой инструкции или строке.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Позиции документа обычно обозначает диапазон строк исходного кода. Этот метод предоставляет начальный и конечный адреса отладки связанных с этими строками. В некоторых языках разрешить инструкций, занимающие несколько строк или строк, содержащих более одной инструкции. Этот метод обеспечивает флаг для ограничения отладки адреса для одной инструкции.  
  
 Это возможно, для одной инструкции использовать несколько адресов отладки, как в случае шаблонов.  
  
## <a name="see-also"></a>См. также  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)