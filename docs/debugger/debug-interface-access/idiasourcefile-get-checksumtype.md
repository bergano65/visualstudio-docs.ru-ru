---
title: IDiaSourceFile::get_checksumType | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d372ad37419d95647a1492503a0b6cabe70ba649
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
Получает тип контрольной суммы.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает тип контрольной суммы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Тип контрольной суммы является значение, которое может быть сопоставлен алгоритма подсчета контрольной суммы. Например стандартный формат файла PDB можно иметь одно из следующих значений:  
  
|Тип контрольной суммы|Метка CryptoAPI|Описание|  
|-------------------|---------------------|-----------------|  
|0|\<None >|Контрольная сумма отсутствует присутствует.|  
|1|`CALG_MD5`|контрольная сумма, созданные с помощью алгоритма хэширования MD5.|  
|2|`CALG_SHA1`|контрольная сумма, созданные с помощью алгоритма хэширования SHA1.|  
  
 `CryptoAPI` Метки принадлежат `ALG_ID` перечисления. Дополнительные сведения о алгоритмы хэширования, обратитесь к `CryptoAPI` части Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Для получения байтов фактическая контрольная сумма исходного файла, вызовите [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)