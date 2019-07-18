---
title: IDiaImageData::get_imageBase | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4a8ed3f52a6e4709aa9553b0d7cc906069c9bcd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202569"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает область памяти, в котором должно основываться изображение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
## <a name="see-also"></a>См. также  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
