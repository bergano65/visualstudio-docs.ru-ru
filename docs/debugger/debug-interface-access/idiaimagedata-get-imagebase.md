---
title: IDiaImageData::get_imageBase | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 0dea0b3e717187bb79525fde0be02d0482e53243
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912666"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
Получает область памяти, в котором должно основываться изображение.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает базовое значение предлагаемые образа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Из-за конфликтов базовый образ образ может изменения перемещены из автоматически опции неиспользуемой памяти при загрузке. Этот метод возвращает базовый указание (Рекомендуемый объем памяти расположение), которое было сохранено в модуле во время компиляции.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)