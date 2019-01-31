---
title: IDiaSectionContrib::get_code | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_code method
ms.assetid: f9ccf7a6-46e7-4a1d-9d5c-97272e17bbbb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1658944b8db6df25111fb8c490b6eeda9ff016ce
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917033"
---
# <a name="idiasectioncontribgetcode"></a>IDiaSectionContrib::get_code
Получает флаг, указывающий, содержит ли раздел исполняемый код.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_code (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает `TRUE` Если раздел содержит исполняемого кода; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)