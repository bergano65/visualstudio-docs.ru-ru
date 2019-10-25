---
title: 'Идиаимажедата:: get_imageBase | Документация Майкрософт'
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
ms.openlocfilehash: 7887fea30b04f4ebb6605169c58551122eccf73d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743440"
---
# <a name="idiaimagedataget_imagebase"></a>IDiaImageData::get_imageBase
Извлекает место в памяти, на котором должно быть основано изображение.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

заполняет Возвращает рекомендуемое базовое значение изображения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Из-за конфликтов базовых образов можно автоматически изменить базовый образ до неиспользуемой памяти при загрузке. Этот метод возвращает базовое указание (рекомендуемое расположение в памяти), которое было сохранено в модуле во время компиляции.

## <a name="see-also"></a>См. также
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)