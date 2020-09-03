---
title: 'IDiaSourceFile:: get_checksumType | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f859bce63e2976b23ab613e249dad41b2bc63486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190704"
---
# <a name="idiasourcefileget_checksumtype"></a>IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает тип контрольной суммы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 заполняет Возвращает тип контрольной суммы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Тип контрольной суммы — это значение, которое может быть сопоставлено с алгоритмом контрольной суммы. Например, стандартный формат PDB-файла обычно может иметь одно из следующих значений:  
  
|Тип контрольной суммы|Метка CryptoAPI|Описание|  
|-------------------|---------------------|-----------------|  
|0|\<none>|Контрольная сумма отсутствует.|  
|1|`CALG_MD5`|Контрольная сумма, созданная с помощью алгоритма хэширования MD5.|  
|2|`CALG_SHA1`|Контрольная сумма, созданная с помощью алгоритма хэширования SHA1.|  
  
 `CryptoAPI`Метки помещаются из `ALG_ID` перечисления. Дополнительные сведения о алгоритмах хэширования см. в `CryptoAPI` разделе корпорации Майкрософт [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)] .  
  
 Чтобы получить фактические байты контрольной суммы для исходного файла, вызовите метод [IDiaSourceFile:: get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)
