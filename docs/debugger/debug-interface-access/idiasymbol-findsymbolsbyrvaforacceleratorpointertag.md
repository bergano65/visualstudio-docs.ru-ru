---
title: "IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f12417323d0553fc6dd9ca33c65c566229454c99
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
Задано значение соответствующего тега, этот метод возвращает перечисление символов, содержащихся в этой функции заглушки указанного относительного виртуального адреса.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### <a name="parameters"></a>Параметры  
 `tagValue`  
 [in] Значение тега указатель, для которого находятся pointee символьные записи.  
  
 `rva`  
 [in] Rva, используемый для фильтрации символы, которые соответствуют pointee переменную с указанным значением тега.  
  
 `ppResult`  
 [out] Указатель на `IDiaEnumSymbols` указатель интерфейса, который инициализируется с результатом.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается только в `IDiaSymbol` интерфейс, который соответствует функции заглушки сочетаний клавиш.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)