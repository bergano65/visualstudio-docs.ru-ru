---
title: IDiaFrameData::get_lengthParams | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthParams method
ms.assetid: a9177ed6-9ba8-4384-b411-24cad07d031b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f633fe4633ba92b1054aec7f516a6a0921bc64ca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563745"
---
# <a name="idiaframedatagetlengthparams"></a>IDiaFrameData::get_lengthParams
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает число байтов параметров в стек.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_lengthParams (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает число байтов параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Значение, возвращаемое этим методом обычно используется в интерпретации строки программы (см. в разделе [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) метод для определения строки программы).  
  
## <a name="see-also"></a>См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
