---
title: 'IDiaLoadCallback2:: Рестрикторигиналпасакцесс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 970a188b5d72353dbb3ccf64fd74f3354f1ba888
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151950"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Определяет, можно ли искать PDB-файл в исходном каталоге отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Любой код возврата, отличный от, `S_OK` не будет искать PDB-файл в исходном каталоге отладки. Исходный каталог отладки — это путь к файлу символов, скомпилированному в исполняемый файл при включенной отладке. Этот путь не обязательно должен совпадать с путем, в котором существует исполняемый файл.  
  
## <a name="see-also"></a>См. также:  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
