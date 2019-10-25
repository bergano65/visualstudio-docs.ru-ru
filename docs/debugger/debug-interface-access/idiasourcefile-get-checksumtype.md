---
title: 'IDiaSourceFile:: get_checksumType | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c85c6ce8f03534c3ed810e530dbd12d8c6d115be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741833"
---
# <a name="idiasourcefileget_checksumtype"></a>IDiaSourceFile::get_checksumType
Возвращает тип контрольной суммы.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_checksumType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

заполняет Возвращает тип контрольной суммы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Тип контрольной суммы — это значение, которое может быть сопоставлено с алгоритмом контрольной суммы. Например, стандартный формат PDB-файла обычно может иметь одно из следующих значений:

|Тип контрольной суммы|Метка CryptoAPI|Описание|
|-------------------|---------------------|-----------------|
|0|\<none>|Контрольная сумма отсутствует.|
|1|`CALG_MD5`|Контрольная сумма, созданная с помощью алгоритма хэширования MD5.|
|2|`CALG_SHA1`|Контрольная сумма, созданная с помощью алгоритма хэширования SHA1.|

 Метки `CryptoAPI` относятся к перечислению `ALG_ID`. Дополнительные сведения о алгоритмах хэширования см. в разделе `CryptoAPI` [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)] Майкрософт.

 Чтобы получить фактические байты контрольной суммы для исходного файла, вызовите метод [IDiaSourceFile:: get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) .

## <a name="see-also"></a>См. также
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)