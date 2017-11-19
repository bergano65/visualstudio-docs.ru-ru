---
title: "IDiaSymbol::get_platform | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_platform method
ms.assetid: dff1c1eb-bcb2-4275-bb07-f2fdc076d6fb
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79e2757ae76f7973def05a1f6468d919cc77347f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetplatform"></a>IDiaSymbol::get_platform
Получает тип платформы, для которой была скомпилирована компилируемого объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_platform (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает значение из [CV_CPU_TYPE_e-перечисление](../../debugger/debug-interface-access/cv-cpu-type-e.md) тип перечисления, указывающее платформу для компилируемого объекта, который был скомпилирован.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md)