---
title: "IDiaEnumDebugStreamData::get_name | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumDebugStreamData::get_Name method
ms.assetid: e6cf2bed-ee2b-4122-886d-c20d93df7ff2
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ebf4e56004bf684edd46cccf977e91fe5ba8a7b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumdebugstreamdatagetname"></a>IDiaEnumDebugStreamData::get_name
Возвращает имя потока данных отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_Name (   
   BSTR * pRetVal  
)  
```  
  
#### <a name="parameters"></a>Параметры  
 pRetVal  
 [out] Возвращает имя потока данных отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)