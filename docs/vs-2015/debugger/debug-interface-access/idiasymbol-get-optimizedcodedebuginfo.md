---
title: IDiaSymbol::get_optimizedCodeDebugInfo | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_optimizedCodeDebugInfo method
ms.assetid: 57ef4170-37a9-46b0-8217-c1a674725113
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d83f7b1b67e2e2aacd0be135fc4e7f3f6e2525fa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558957"
---
# <a name="idiasymbolgetoptimizedcodedebuginfo"></a>IDiaSymbol::get_optimizedCodeDebugInfo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaSymbol::get_optimizedCodeDebugInfo](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo).  
  
Получает флаг, указывающий, содержит ли функция отладочной информации, характерное для оптимизированного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT get_optimizedCodeDebugInfo(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pFlag`  
 [out] Возвращает `TRUE` Если Оптимизированная функция или метка содержит сведения об отладке; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



