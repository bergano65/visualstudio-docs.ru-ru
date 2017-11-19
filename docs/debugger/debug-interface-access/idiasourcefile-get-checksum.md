---
title: "IDiaSourceFile::get_checksum | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2bcfbc701f6f4799a51d09fac4c4eb184e6f5d7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
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
 [in] Размер буфера данных, в байтах.  
  
 `pcbData`  
 [out] Возвращает число байтов контрольной суммы. Этот параметр не может быть `NULL`.  
  
 `data`  
 [in, out] Буфер, заполненный байт контрольной суммы. Если этот параметр имеет `NULL`, затем `pcbData` возвращает число байтов, необходимое.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Чтобы определить тип алгоритма подсчета контрольной суммы, которая использовалась при создании контрольной суммы байт, вызовите [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) метод.  
  
 Контрольная сумма обычно создается из образа исходного файла, поэтому изменения в исходном файле отражаются изменения в байтах контрольной суммы. Если байт контрольной суммы не совпадают контрольной суммы, созданные из загруженного файла, изображения, то файл считается поврежден или подделан.  
  
 Обычно контрольные суммы не более 32 байта, но не следует предполагать, что максимальный размер контрольной суммы. Задать `data` параметр `NULL` дает число байтов, необходимых для получения контрольной суммы. Затем выделить буфер соответствующий размер и вызвать этот метод еще раз с помощью нового буфера.  
  
## <a name="see-also"></a>См. также  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)