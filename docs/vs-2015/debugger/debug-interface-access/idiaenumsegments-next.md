---
title: IDiaEnumSegments::Next | Документация Майкрософт
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
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f96f6d388b151e027c9795d6042b88d8f1e65091
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559876"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaEnumSegments::Next](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumsegments-next).  
  
Возвращает указанное количество сегментов в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Next (   
   ULONG         celt,   
   IDiaSegment** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 [in] Количество сегментов в перечислителе требуется получить.  
  
 rgelt  
 [out] Массив, который должен быть заполнен с требуемым [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) объекты, представляющие сегменты.  
  
 pceltFetched  
 [out] Возвращает число сегментов в выбранных перечислитель.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`. Возвращает `S_FALSE` при наличии не больше сегментов. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)



