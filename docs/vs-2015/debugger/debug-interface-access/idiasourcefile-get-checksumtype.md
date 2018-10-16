---
title: IDiaSourceFile::get_checksumType | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d4fc1528bc7746547b5351ee93a7789e128703c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260290"
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает тип контрольной суммы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает тип контрольной суммы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Тип контрольной суммы — значение, которое может быть сопоставлен алгоритма подсчета контрольной суммы. Например стандартные PDB-файлов можно обычно имеют один из следующих значений:  
  
|Тип контрольной суммы|Метка CryptoAPI|Описание|  
|-------------------|---------------------|-----------------|  
|0|\<None >|Контрольная сумма не существует.|  
|1|`CALG_MD5`|контрольная сумма, созданных с использованием алгоритма хэширования MD5.|  
|2|`CALG_SHA1`|контрольная сумма, созданных с использованием алгоритма хэширования SHA1.|  
  
 `CryptoAPI` Метки являются из `ALG_ID` перечисления. Дополнительные сведения о алгоритмы хэширования, обратитесь к `CryptoAPI` раздел Microsoft [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)].  
  
 Чтобы получить байты фактическая контрольная сумма для исходного файла, вызовите [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)



