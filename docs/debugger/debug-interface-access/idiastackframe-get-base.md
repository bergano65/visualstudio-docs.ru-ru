---
title: IDiaStackFrame::get_base | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_base method
ms.assetid: f27477d7-26fe-4c1c-a08a-c52cb20c8293
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4053a49b0b0a4ebf55e55f0633672d98c2f02ce
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975209"
---
# <a name="idiastackframegetbase"></a>IDiaStackFrame::get_base
Получает базовый адрес кадра.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_base (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает базовый адрес.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)