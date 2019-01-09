---
title: IDiaLoadCallback2::RestrictOriginalPathAccess | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b88ea861c34eef8761b22cdc4c23f4e79a6b978
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872304"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Определяет, разрешается ли для поиска PDB-файл в исходном каталоге отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Любой код возврата не `S_OK` не позволяет найти PDB-файл в исходном каталоге отладки. Исходный каталог отладки — путь к файлу символов, компилируется в исполняемый файл, если отладка включена. Этот путь не обязательно так же, как путь, где существует исполняемый файл.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)