---
title: 'IDiaLoadCallback2:: Рестриктдбгакцесс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictDBGAccess method
ms.assetid: 63b67a93-2910-4fff-aa70-6b2eaa08e5c8
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3c40aca343821f26213ee9e609a341918b9a7ba9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187313"
---
# <a name="idialoadcallback2restrictdbgaccess"></a>IDiaLoadCallback2::RestrictDBGAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Определяет, разрешена ли информация об отладке из DBG-файлов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT RestrictDBGAccess();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Любое возвращаемое значение, отличное от `S_OK` , для предотвращения поиска отладочных данных из файлов dbg.  
  
## <a name="see-also"></a>См. также:  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
