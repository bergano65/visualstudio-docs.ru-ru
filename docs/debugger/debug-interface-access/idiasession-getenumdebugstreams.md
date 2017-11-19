---
title: "IDiaSession::getEnumDebugStreams | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::getEnumDebugStreams method
ms.assetid: d294954b-80e9-476c-b9f0-5ca6fd575f68
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf7025f4a9fb9bef9f8980ae04bf0c8cae056df5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessiongetenumdebugstreams"></a>IDiaSession::getEnumDebugStreams
Возвращает перечислимый последовательности отладки потоков данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT getEnumDebugStreams (   
   IDiaEnumDebugStreams** ppEnumDebugStreams  
)  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnumDebugStreams`  
 [out] Возвращает [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md) , содержащий список потоки отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)