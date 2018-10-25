---
title: IDiaEnumSegments::Item | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f7d98e160f3a0723293ce8349f475bf6519ed51
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913700"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает сегмент с помощью индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Item (   
   DWORD         index,  
   IDiaSegment** segment  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 индекс  
 [in] Индекс [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) извлекаемый объект. Индекс находится в диапазоне от 0 до `count`-1, где `count` возвращается [IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md) метод.  
  
 Сегмент  
 [out] Возвращает [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) объект, представляющий нужного сегмента.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)



