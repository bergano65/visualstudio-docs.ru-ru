---
title: IDiaSession::findInjectedSource | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 11a4134ce02ca540cdffff9cc51a1280bd4173bf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978517"
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает список источников, размещенных в хранилище символов поставщиками атрибут или другие компоненты в процессе компиляции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findInjectedSource (   
   LPCOLESTR                 srcFile,  
   IDiaEnumInjectedSources** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 srcFile  
 [in] Имя исходного файла, который требуется найти.  
  
 ppResult  
 [out] Возвращает [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) , содержащий список всех внедренного источников.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
