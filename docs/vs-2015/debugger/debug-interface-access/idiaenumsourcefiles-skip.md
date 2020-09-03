---
title: 'IDiaEnumSourceFiles:: Skip | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Skip method
ms.assetid: 4821e6dd-d33f-403d-857d-e3ae81e4a9e3
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 14bfe8762d914770dd2523a431bada883d003511
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189770"
---
# <a name="idiaenumsourcefilesskip"></a>IDiaEnumSourceFiles::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пропускает указанное число исходных файлов в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 окне Число пропускаемых исходных файлов в последовательности перечисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает значение `S_OK` ; в противном случае возвращает значение, `S_FALSE` Если нет других исходных файлов для пропуска.  
  
## <a name="see-also"></a>См. также:  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
