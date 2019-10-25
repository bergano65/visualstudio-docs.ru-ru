---
title: 'IDiaSourceFile:: get_checksum | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f4367a7862dabe248dfbe08e64c45598abe3679
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741835"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
Получает байты контрольной суммы.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_checksum ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Параметры
 `cbData`

окне Размер буфера данных в байтах.

 `pcbData`

заполняет Возвращает число байтов контрольной суммы. Этот параметр не может быть `NULL`.

 `data`

[вход, выход] Буфер, который заполняется байтами контрольной суммы. Если этот параметр имеет значение `NULL`, `pcbData` возвращает необходимое число байтов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Чтобы определить тип алгоритма контрольной суммы, который использовался для формирования байтов контрольной суммы, вызовите метод [IDiaSourceFile:: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) .

 Контрольная сумма обычно создается на основе образа исходного файла, поэтому изменения в исходном файле отражаются в изменениях контрольной суммы. Если контрольная сумма байтов не совпадает с контрольной суммой, созданной на основе загруженного образа файла, то файл должен считаться поврежденным или незаконным.

 Обычные контрольные суммы не должны превышать 32 байт, но не предполагается, что является максимальным размером контрольной суммы. Задайте для параметра `data` значение `NULL`, чтобы получить число байтов, необходимых для получения контрольной суммы. Затем выделите буфер соответствующего размера и вызовите этот метод еще раз с новым буфером.

## <a name="see-also"></a>См. также
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)