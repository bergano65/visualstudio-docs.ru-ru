---
title: 'IDiaFrameData:: get_lengthLocals | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthLocals method
ms.assetid: 51fe15c3-4cd6-4a06-8a41-a56502209762
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da9c50b6c63176fdb3156b2daa15d6c0e1bbefbb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62552570"
---
# <a name="idiaframedataget_lengthlocals"></a>IDiaFrameData::get_lengthLocals
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает число байтов локальных переменных, отправленных в стек.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_lengthLocals (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 заполняет Возвращает число байтов локальных переменных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Значение, возвращаемое этим методом, обычно используется при интерпретации строки программы (см. метод [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) для определения программной строки).  
  
## <a name="see-also"></a>См. также:  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
