---
title: IDiaSourceFile::get_checksum | Документация Майкрософт
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
ms.openlocfilehash: f02338f46ace5da0d7769a6b27bc3500b797a9be
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977659"
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
Извлекает байты контрольной суммы.  
  
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
 [in] Размер буфера данных, в байтах.  
  
 `pcbData`  
 [out] Возвращает число байтов контрольной суммы. Этот параметр не может быть `NULL`.  
  
 `data`  
 [in, out] Буфер, который заполняется байты контрольной суммы. Если этот параметр имеет `NULL`, затем `pcbData` возвращает число байтов, необходимых.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Чтобы определить тип алгоритма подсчета контрольной суммы, который использовался для создания байты контрольной суммы, вызовите [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) метод.  
  
 Контрольная сумма обычно создается из образа исходного файла, поэтому изменения в исходном файле отражаются изменения в байты контрольной суммы. Если байты контрольной суммы не совпадают контрольной суммы, созданный из загруженного образа файла, а затем файл можно рассматривать поврежден или подделан.  
  
 Обычно контрольные суммы не более чем 32 байта, но не следует предполагать, что это максимальный размер контрольной суммы. Задайте `data` параметр `NULL` получить число байтов, необходимых для получения контрольной суммы. Затем выделить буфер соответствующего размера и вызвать этот метод еще раз с помощью нового буфера.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)