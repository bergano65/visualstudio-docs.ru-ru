---
title: "IDiaLoadCallback::RestrictSymbolServerAccess | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback::RestrictSymbolServerAccess method
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa536c1a63abe6a58b6b92edb4f39343191f1796
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
Определяет, если доступ будет разрешен на сервере символов для разрешения символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT RestrictSymbolServerAccess();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Любой код возврата не `S_OK` запрещено использование сервера символов для разрешения символов.  
  
## <a name="see-also"></a>См. также  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)