---
title: IDiaEnumInjectedSources::Next | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Next method
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be10fda2348d0fb578cd5804bc72b02c897cb58d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiaenuminjectedsourcesnext"></a>IDiaEnumInjectedSources::Next
Извлекает указанное число подставляемого источников в последовательность перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Next (   
   ULONG                celt,   
   IDiaInjectedSource** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 [in] Число подставляемого источников перечислителя, который требуется получить.  
  
 rgelt  
 [out] Возвращает массив [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) объекты, которые представляют требуемой подставляемого источников.  
  
 pceltFetched  
 [out] Возвращает число подставляемого источников извлеченных перечислителя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если больше нет подставляемого источников. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)