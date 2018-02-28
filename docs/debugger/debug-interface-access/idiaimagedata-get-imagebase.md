---
title: "IDiaImageData::get_imageBase | Документы Microsoft"
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
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5e3730e7bc543d0b7bdea18e162dfe83e1d803bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
Получает области памяти, где должно быть основано изображения.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает значение базового предлагаемые изображения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Из-за конфликтов базового образа изображение может быть перемещен автоматически к размещению неиспользуемую память при ее загрузке. Этот метод возвращает базовый указание (расположение Рекомендуемый объем памяти), которое было сохранено в модуле во время компиляции.  
  
## <a name="see-also"></a>См. также  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)