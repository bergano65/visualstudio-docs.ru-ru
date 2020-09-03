---
title: 'IDiaSourceFile:: get_checksum | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f87f5cdd937c0e172e7b96cf0858423b14686d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190741"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает байты контрольной суммы.  
  
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
 окне Размер буфера данных в байтах.  
  
 `pcbData`  
 заполняет Возвращает число байтов контрольной суммы. Этот параметр не может иметь значение `NULL`.  
  
 `data`  
 [вход, выход] Буфер, который заполняется байтами контрольной суммы. Если этот параметр имеет значение `NULL` , то функция `pcbData` возвращает требуемое число байтов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Чтобы определить тип алгоритма контрольной суммы, который использовался для формирования байтов контрольной суммы, вызовите метод [IDiaSourceFile:: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) .  
  
 Контрольная сумма обычно создается на основе образа исходного файла, поэтому изменения в исходном файле отражаются в изменениях контрольной суммы. Если контрольная сумма байтов не совпадает с контрольной суммой, созданной на основе загруженного образа файла, то файл должен считаться поврежденным или незаконным.  
  
 Обычные контрольные суммы не должны превышать 32 байт, но не предполагается, что является максимальным размером контрольной суммы. Задайте для `data` параметра значение, `NULL` чтобы получить число байтов, необходимых для получения контрольной суммы. Затем выделите буфер соответствующего размера и вызовите этот метод еще раз с новым буфером.  
  
## <a name="see-also"></a>См. также:  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)
