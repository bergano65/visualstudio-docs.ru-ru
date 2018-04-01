---
title: IDiaSymbol::get_isSingleInheritance | Документы Microsoft
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
ms.assetid: 46cde656-059b-4c20-9476-3ca68ccc9912
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4481fd4517db89867ca21b137af454980f60de26
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetissingleinheritance"></a>IDiaSymbol::get_isSingleInheritance
Указывает, является ли `this` указатель указывает на данные-член с единичным наследованием.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_isSingleInheritance(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Указатель на `BOOL` , указывает ли `this` указатель указывает на данные-член с единичным наследованием.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)