---
title: "IDiaEnumSegments::Skip | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSegments::Skip method
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72f327dc469eef73e560df6da83ce65c038cff0c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
Пропускает указанное число сегментов в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 [in] Количество сегментов в последовательность перечисления для пропуска.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` при наличии не больше сегментов, чтобы пропустить.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)