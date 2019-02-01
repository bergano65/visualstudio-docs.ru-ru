---
title: IDiaEnumSegments::Item | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e9e1632fa9031dc502cce6467e60e76d30bf874
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999045"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
Возвращает сегмент с помощью индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Item (   
   DWORD         index,  
   IDiaSegment** segment  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 индекс  
 [in] Индекс [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) извлекаемый объект. Индекс находится в диапазоне от 0 до `count`-1, где `count` возвращается [IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md) метод.  
  
 сегмент  
 [out] Возвращает [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) объект, представляющий нужного сегмента.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)