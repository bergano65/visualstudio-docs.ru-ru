---
title: IDiaSectionContrib::get_nopad | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 694925b51d2cb65d4a3e1f38b54c20926b5895c7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910913"
---
# <a name="idiasectioncontribgetnopad"></a>IDiaSectionContrib::get_nopad
Получает флаг, указывающее, является ли раздел не будут заполнены до следующей границы памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_nopad(  
   BOOL* pRetVal  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает `TRUE` Если разделе должно быть заполнено до следующей границы памяти; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Это свойство обычно появляется только на старых файлов.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)