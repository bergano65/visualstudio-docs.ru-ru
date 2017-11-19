---
title: "IDiaSourceFile::get_compilands | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSourceFile::get_compilands method
ms.assetid: 57deb50a-9c22-43ea-a80c-eab205997bc4
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b351419b3331c318c6ebc1522d4e5912adae0ce9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasourcefilegetcompilands"></a>IDiaSourceFile::get_compilands
Извлекает перечислитель компилируемые объекты, номера строки, ссылающиеся на этот файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_compilands (   
   IDiaEnumSymbols** ppRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppRetVal`  
 [out] Возвращает [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) , содержащий список всех компилируемые объекты, имеющие номера строки, ссылающиеся на этот файл.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)