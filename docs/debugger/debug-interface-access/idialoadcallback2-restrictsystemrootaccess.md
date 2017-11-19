---
title: "IDiaLoadCallback2::RestrictSystemRootAccess | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback2::RestrictSystemRootAccess method
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2f77f92487f8f44aa2608f6e29eb779c9292ae8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idialoadcallback2restrictsystemrootaccess"></a>IDiaLoadCallback2::RestrictSystemRootAccess
Определяет, разрешено при поиске PDB-файлы в корневом каталоге системы.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT RestrictSystemRootAccess();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Любой код возврата не `S_OK` предотвращает поиска к корневой папке системы PDB-файлов.  
  
## <a name="see-also"></a>См. также  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)