---
title: 'Идебугсимболпровидер:: Жетаддрессесфромпоситион | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27349cfdc438da133c4cea05077649ebb4df376c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547160"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод сопоставляет расположение документа с массивом адресов отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Расположение документа.  
  
 `fStatmentOnly`  
 окне Если значение — TRUE, адреса отладки ограничиваются одной инструкцией.  
  
 `ppEnumBegAddresses`  
 заполняет Возвращает перечислитель для начальных адресов отладки, связанных с данной инструкцией или строкой.  
  
 `ppEnumEndAddresses`  
 заполняет Возвращает перечислитель [иенумдебугаддрессес](../../../extensibility/debugger/reference/ienumdebugaddresses.md) для конечных адресов отладки, связанных с данной инструкцией или строкой.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Расположение документа обычно указывает на диапазон исходных строк. Этот метод предоставляет начальный и конечный отладочные адреса, связанные с этими строками. Некоторые языки разрешают операторы, охватывающие несколько строк, или строки, содержащие более одной инструкции. Этот метод предоставляет флаг для ограничения адресов отладки одной инструкцией.  
  
 Одна инструкция может иметь несколько отладочных адресов, как в случае с шаблонами.  
  
## <a name="see-also"></a>См. также:  
 [идебугсимболпровидер](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [жетаддрессесфромконтекст](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
