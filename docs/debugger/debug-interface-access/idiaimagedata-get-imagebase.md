---
title: IDiaImageData::get_imageBase | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 032ff3cee51c3c8295395aba6e9e60bfa4e9a400
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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