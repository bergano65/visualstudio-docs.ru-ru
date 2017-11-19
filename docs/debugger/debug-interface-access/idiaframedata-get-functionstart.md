---
title: "IDiaFrameData::get_functionStart | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51303607eace37d5886c14efc1057bc50e4c8ce0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiaframedatagetfunctionstart"></a>IDiaFrameData::get_functionStart
Возвращает флаг, указывающий, является ли блок содержит точку входа функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_functionStart (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает `TRUE` Если блок содержит точку входа; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Это возможно для кадра стека не является начала функции из-за рамки представляет встроенный метод или функция, вставляемых в функции.  
  
## <a name="see-also"></a>См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)