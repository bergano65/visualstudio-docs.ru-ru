---
title: IDiaSymbol::get_isMultipleInheritance | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0aa356a1-5c5c-4ee4-8b48-bae0a2610013
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51ebecb18b8a96560bc89f02f8f5559d300e2318
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgetismultipleinheritance"></a>IDiaSymbol::get_isMultipleInheritance
Указывает, является ли `this` указатель указывает на данные-член с множественным наследованием.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_isMultipleInheritance(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Указатель на `BOOL` , указывает ли `this` указатель указывает на данные-член с множественным наследованием.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)