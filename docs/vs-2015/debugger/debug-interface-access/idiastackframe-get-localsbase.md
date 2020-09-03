---
title: 'IDiaStackFrame:: get_localsBase | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_localsBase method
ms.assetid: eb0bd73e-d92d-468e-a0b1-fbc279919f54
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5b21f7cf8a877c1faab8d9535960a116a8f6bb6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190532"
---
# <a name="idiastackframeget_localsbase"></a>IDiaStackFrame::get_localsBase
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает базовый адрес локальных переменных для рамки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_localsBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 заполняет Возвращает базовый адрес локальных переменных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает значение, `S_FALSE` Если свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
