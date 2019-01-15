---
title: IDiaLineNumber::get_length | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_length method
ms.assetid: 2c55a6f7-4ef5-45fb-9fd1-d72deaaa2829
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 34e36486f95964169200cee7c41ac8eaebc27960
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916417"
---
# <a name="idialinenumbergetlength"></a>IDiaLineNumber::get_length
Возвращает число байтов в блоке.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_length (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает число байтов в блоке.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Блок является длина исходного кода в строке, представленные как [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) объекта.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)