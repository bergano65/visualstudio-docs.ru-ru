---
title: IDiaSession::findInjectedSource | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af1eba03b231bf894084090a191432c64bedc861
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
Возвращает список источников, который был помещен в хранилище символов поставщиками атрибута или другие компоненты в процессе компиляции.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findInjectedSource (   
   LPCOLESTR                 srcFile,  
   IDiaEnumInjectedSources** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 srcFile  
 [in] Имя исходного файла, который требуется найти.  
  
 ppResult  
 [out] Возвращает [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) , содержащий список всех подставляемого источников.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)