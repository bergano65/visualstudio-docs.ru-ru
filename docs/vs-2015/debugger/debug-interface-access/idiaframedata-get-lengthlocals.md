---
title: IDiaFrameData::get_lengthLocals | Документация Майкрософт
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
- IDiaFrameData::get_lengthLocals method
ms.assetid: 51fe15c3-4cd6-4a06-8a41-a56502209762
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66d70767c21f253064011752f965973efa885ab2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746777"
---
# <a name="idiaframedatagetlengthlocals"></a>IDiaFrameData::get_lengthLocals
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает число байтов в стек локальных переменных.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_lengthLocals (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает число байтов, локальных переменных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Значение, возвращаемое этим методом обычно используется в интерпретации строки программы (см. в разделе [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) метод для определения строки программы).  
  
## <a name="see-also"></a>См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)



