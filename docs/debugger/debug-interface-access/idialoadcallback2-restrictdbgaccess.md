---
title: IDiaLoadCallback2::RestrictDBGAccess | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictDBGAccess method
ms.assetid: 63b67a93-2910-4fff-aa70-6b2eaa08e5c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da2f8312b67610a1f796e6bf9949d24a195428d4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55016523"
---
# <a name="idialoadcallback2restrictdbgaccess"></a>IDiaLoadCallback2::RestrictDBGAccess
Определяет, если может найти отладочную информацию из DBG-файлы.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT RestrictDBGAccess();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Любое возвращаемое значение, отличное от `S_OK` во избежание найти отладочную информацию из DBG-файлы.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)