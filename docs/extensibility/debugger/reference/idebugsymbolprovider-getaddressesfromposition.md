---
title: IDebugSymbolProvider::GetAddressesFromPosition | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 42d82f444e861fe9eaf3b377828c2cce511c3adb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838950"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Этот метод сопоставляет позицию документов в массив адресов отладки.  
  
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
 [in] Если значение равно TRUE, ограничивает адреса отладки для одной инструкции.  
  
 `ppEnumBegAddresses`  
 [out] Возвращает перечислитель для начала отладки адреса, связанные с этой инструкции или строке.  
  
 `ppEnumEndAddresses`  
 [out] Возвращает [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) перечислитель для конечного адреса отладки, связанные с этой инструкции или строке.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Позиция в документе обычно обозначает диапазон строк источника. Этот метод содержит начальный и конечный адреса отладки связанных с такими строками. Некоторые языки допускают инструкций, которые охватывают несколько строк или строк, содержащих более одной инструкции. Этот метод предоставляет флаг для ограничения отладки адреса для одной инструкции.  
  
 Вполне возможно, для одной инструкции иметь несколько адресов отладки, как и в случае шаблонов.  
  
## <a name="see-also"></a>См. также  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)