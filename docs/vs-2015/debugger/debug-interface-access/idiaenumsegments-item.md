---
title: 'Идиаенумсегментс:: Item | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e69c8123af3ac9061141058d5eb41178e5cd0e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189897"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает сегмент с помощью индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Item (   
   DWORD         index,  
   IDiaSegment** segment  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 index  
 окне Индекс объекта [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) для извлечения. Индекс находится в диапазоне от 0 до `count` -1, где `count` возвращается методом [идиаенумсегментс:: get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md) .  
  
 сегмент  
 заполняет Возвращает объект [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , представляющий нужный сегмент.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [идиаенумсегментс](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
