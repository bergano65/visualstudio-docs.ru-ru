---
title: "IDiaEnumLineNumbers::Next | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumLineNumbers::Next method
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 627a6e2dd0e319cbcdccfa5824d9c379faa0d049
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumlinenumbersnext"></a>IDiaEnumLineNumbers::Next
Возвращает указанное количество номеров строк в порядке перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Next (   
   ULONG            celt,  
   IDiaLineNumber** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 [in] Количество номеров строк в перечислителе требуется получить.  
  
 rgelt  
 [out] Возвращает массив [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) объекты, представляющие номера нужной строке.  
  
 pceltFetched  
 [out] Возвращает количество номеров строк в выбранных перечислителя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` при наличии без дополнительных номеров строк. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)