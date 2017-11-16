---
title: "Функция CvLeaveSpan | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkers/CvLeaveSpan
helpviewer_keywords: CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1886858cfedbb3651a394b9f739feadd6c77d1a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="cvleavespan-function"></a>Функция CvLeaveSpan
Отмечает конец диапазона.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CvLeaveSpan(  
   _In_ PCV_SPAN pSpan  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pSpan`  
 Объект диапазона, возвращенный во время предыдущего вызова CvEnterSpan *. Не может принимать значение NULL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение S_OK, если сообщение успешно записано. Код ошибки в том случае, если были какие-либо ошибки. Для проверки условия ошибки используйте макрос SUCCEEDED/FAILED.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** cvmarkers.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по библиотеке C++](../profiling/cpp-library-reference.md)