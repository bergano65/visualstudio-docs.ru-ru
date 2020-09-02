---
title: 'IDiaLoadCallback2:: Рестриктреференцепасакцесс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ce0f2b896b60a13635818249e9faf552f3070828
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187302"
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Определяет, разрешен ли PDB-файл в пути, где находится EXE-файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT RestrictReferencePathAccess();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Любой код возврата, отличный от `S_OK` , для предотвращения поиска PDB-файла в пути, где находится EXE-файл.  
  
## <a name="see-also"></a>См. также:  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
