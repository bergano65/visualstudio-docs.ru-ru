---
title: IDiaStackFrame::get_allocatesBasePointer | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_allocatesBasePointer
ms.assetid: a91e9c8e-c5e3-4887-a60b-f03b5a98f30c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f73123d4dec9a2df7dace087d5b3147110ca6ea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190639"
---
# <a name="idiastackframegetallocatesbasepointer"></a>IDiaStackFrame::get_allocatesBasePointer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает флаг, указывающий тип базового указателя, выделяемые для кода в этот диапазон адресов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает `TRUE` Если базового указателя выделяется для кода в данном фрейме; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
