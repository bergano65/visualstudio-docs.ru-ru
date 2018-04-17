---
title: IDiaEnumSegments::get_Count | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::get_Count method
ms.assetid: c62a0fda-17b8-4cf6-b321-6014ce581096
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6cb4080c678d07b75da6cf00e8c6ba273af9cf49
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiaenumsegmentsgetcount"></a>IDiaEnumSegments::get_Count
Возвращает число сегментов.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_Count (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pRetVal  
 [out, retval] Возвращает число сегментов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)