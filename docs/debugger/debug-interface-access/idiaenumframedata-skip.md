---
title: "IDiaEnumFrameData::Skip | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3284b550d2c55780fa4cc840645113d5c48df09f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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