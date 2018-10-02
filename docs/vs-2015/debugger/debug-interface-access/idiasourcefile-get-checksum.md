---
title: IDiaSourceFile::get_checksum | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4c8ce89bd4cfe42be0fc67897a4545ecbe6a8a2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571134"
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaSourceFile::get_checksum](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasourcefile-get-checksum).  
  
Извлекает байты контрольной суммы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
## <a name="see-also"></a>См. также  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)



