---
title: 'Идиаимажедата:: get_imageBase | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202569"
---
# <a name="idiaimagedataget_imagebase"></a>IDiaImageData::get_imageBase
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает место в памяти, на котором должно быть основано изображение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 заполняет Возвращает рекомендуемое базовое значение изображения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Из-за конфликтов базовых образов можно автоматически изменить базовый образ до неиспользуемой памяти при загрузке. Этот метод возвращает базовое указание (рекомендуемое расположение в памяти), которое было сохранено в модуле во время компиляции.  
  
## <a name="see-also"></a>См. также:  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
