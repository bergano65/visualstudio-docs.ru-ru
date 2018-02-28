---
title: "IDiaEnumFrameData::Skip | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cbfd05b64ba1a04c4e98e137c0d70787f01575fa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
Пропускает указанное число элементов данных кадра в порядке перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 [in] Число кадров данных элементов в последовательности перечисления для пропуска.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` Если нет дополнительных записей для пропуска.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)