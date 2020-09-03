---
title: 'Идебугсимболпровидер:: Жетаддрессесфромконтекст | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebd36bdda5059a4fd3c0334a5a2f222aaae40f01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68206012"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод сопоставляет контекст документа с массивом адресов отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Контекст документа.  
  
 `fStatmentOnly`  
 окне Если значение — TRUE, адреса отладки ограничиваются одной инструкцией.  
  
 `ppEnumBegAddresses`  
 заполняет Возвращает перечислитель для начальных адресов отладки, связанных с данной инструкцией или строкой.  
  
 `ppEnumEndAddresses`  
 заполняет Возвращает перечислитель [иенумдебугаддрессес](../../../extensibility/debugger/reference/ienumdebugaddresses.md) для конечных адресов отладки, связанных с данной инструкцией или строкой.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Контекст документа обычно указывает на диапазон исходных строк. Этот метод предоставляет начальный и конечный отладочные адреса, связанные с этими строками. Некоторые языки разрешают операторы, охватывающие несколько строк, или строки, содержащие более одной инструкции. Этот метод предоставляет флаг для ограничения адресов отладки одной инструкцией.  
  
 Одна инструкция может иметь несколько отладочных адресов, как в случае с шаблонами.  
  
## <a name="see-also"></a>См. также:  
 [идебугсимболпровидер](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [жетаддрессесфромпоситион](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
