---
title: "IDiaFrameData::get_systemExceptionHandling | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_systemExceptionHandling method
ms.assetid: e8df1972-913c-446c-9779-775575b0caa9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 00f16f6d916d14319c9ec4d8d009188952fe9e13
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiaframedatagetsystemexceptionhandling"></a>IDiaFrameData::get_systemExceptionHandling
Возвращает флаг, который указывает, является ли система обработки исключений в силе.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_systemExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pRetVal  
 [out] Возвращает `TRUE` в случае обработки исключений системы действует; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Обработка исключений системы более часто называется структурированной обработки исключений.  
  
 Чтобы определить, действует ли обработка исключений с ++, вызовите [IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)