---
title: IDiaStackFrame::get_size | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_size method
ms.assetid: 71e2f5ab-4aa8-4922-aa8a-b7db97ee143c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0f646dd6bfe93835d2d30280c7e57e7de2fbefa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190509"
---
# <a name="idiastackframegetsize"></a>IDiaStackFrame::get_size
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает размер кадра стека в байтах.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_size (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает размер кадра стека в байтах.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
