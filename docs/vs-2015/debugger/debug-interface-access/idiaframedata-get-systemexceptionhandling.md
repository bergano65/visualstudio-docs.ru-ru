---
title: 'IDiaFrameData:: get_systemExceptionHandling | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_systemExceptionHandling method
ms.assetid: e8df1972-913c-446c-9779-775575b0caa9
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ba6bddf905834f711cfcd5ab9606420e9fbfa6b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161449"
---
# <a name="idiaframedataget_systemexceptionhandling"></a>IDiaFrameData::get_systemExceptionHandling
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает флаг, указывающий, действует ли обработка системных исключений.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_systemExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 претвал  
 заполняет Возвращает значение `TRUE` , если обрабатывается Системное исключение. в противном случае возвращает `FALSE` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Обработка системных исключений чаще известна как структурированная обработка исключений.  
  
 Чтобы определить, действует ли обработка исключений C++, вызовите метод [IDiaFrameData:: get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)
