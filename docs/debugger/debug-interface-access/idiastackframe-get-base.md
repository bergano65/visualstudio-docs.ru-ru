---
title: "IDiaStackFrame::get_base | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackFrame::get_base method
ms.assetid: f27477d7-26fe-4c1c-a08a-c52cb20c8293
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26449893366c5c63892349976ef5db1c47dd8036
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackframegetbase"></a>IDiaStackFrame::get_base
Возвращает базовый адрес кадра.  
  
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
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)