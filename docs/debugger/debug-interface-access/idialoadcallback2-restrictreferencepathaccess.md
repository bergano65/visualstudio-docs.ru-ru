---
title: IDiaLoadCallback2::RestrictReferencePathAccess | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f05babd6e7abb83362eef01a59e3ab93bbcb925f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029618"
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
Определяет, разрешено при поиске PDB-файл в каталоге, где находится файл .exe.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT RestrictReferencePathAccess();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Любой код возврата не `S_OK` во избежание поиск PDB-файл в путь, где находится файл .exe.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)