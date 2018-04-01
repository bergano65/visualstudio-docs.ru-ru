---
title: IDiaSymbol::get_registerType | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: f1c98ab0-8aef-4a07-a686-28b8a54418ef
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b6ed4fb8ad9d50ca54174ff4794097b378173630
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetregistertype"></a>IDiaSymbol::get_registerType
Возвращает тип регистра.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_registerType(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Указатель на `DWORD` , содержащий тип регистра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)