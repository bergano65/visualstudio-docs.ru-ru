---
title: IDiaStackFrame::get_type | Документы Microsoft
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
helpviewer_keywords:
- IDiaStackFrame::get_type method
ms.assetid: 99daa97b-5c05-455d-bd1e-800762ccf7c9
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1d5d31b1d10db7167224c7b84f5ba7eb6ad1ccef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackframegettype"></a>IDiaStackFrame::get_type
Получает тип пакета.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает значение из [stackframetypeenum-перечисление](../../debugger/debug-interface-access/stackframetypeenum.md) перечисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [Перечисление StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md)