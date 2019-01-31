---
title: IDiaLineNumber::get_columnNumber | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumber method
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01f8442c12cdbe31111967bd04e2af6d091e36b6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925784"
---
# <a name="idialinenumbergetcolumnnumber"></a>IDiaLineNumber::get_columnNumber
Получает номер столбца, где начинается выражения или оператора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
[C++]  
HRESULT get_columnNumber (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает номер столбца, где начинается выражения или оператора. Если значение равно нулю, сведения о столбце отсутствует.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Значение столбца, возвращаемого этим методом, — это смещение в байтах в строке до первого символа в строке инструкции.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)