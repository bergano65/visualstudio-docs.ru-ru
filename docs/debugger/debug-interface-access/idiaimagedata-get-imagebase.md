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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de8c333391530cd86c6fc66a8e6c36ce8cfecd5f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623870"
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
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)