---
title: "IDebugSymbolProvider::GetAddressesFromContext | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords: IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d2499fb1cca7dcbbf278d00c0aac205774d3cb75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Этот метод сопоставляет массив адресов отладки к контексту документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pDocContext`  
 [in] Контекст документа.  
  
 `fStatmentOnly`  
 [in] Если значение равно TRUE, ограничивает отладки адреса для одной инструкции.  
  
 `ppEnumBegAddresses`  
 [out] Возвращает перечислитель для начала отладки адреса, связанные с этой инструкции или строке.  
  
 `ppEnumEndAddresses`  
 [out] Возвращает [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) перечислитель для конечного адреса отладки, связанные с этой инструкции или строке.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Контексту документа обычно обозначает диапазон строк исходного кода. Этот метод предоставляет начальный и конечный адреса отладки связанных с этими строками. В некоторых языках разрешить инструкций, занимающие несколько строк или строк, содержащих более одной инструкции. Этот метод обеспечивает флаг для ограничения отладки адреса для одной инструкции.  
  
 Это возможно, для одной инструкции использовать несколько адресов отладки, как в случае шаблонов.  
  
## <a name="see-also"></a>См. также  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)