---
title: "IDiaSymbol::get_isLTCG | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9be567714b30eea80579836b2a596bbf4f872e3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetisltcg"></a>IDiaSymbol::get_isLTCG
Возвращает флаг, указывающий ли [компилируемого объекта](../../debugger/debug-interface-access/compiland.md) связан с параметром компоновщика [/LTCG (Создание кода во время компоновки)](/cpp/build/reference/ltcg-link-time-code-generation), который помогает при оптимизации всей программы. Этот параметр применяется только к управляемому коду.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_iSLTCG(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pFlag  
 [out] Возвращает `TRUE` Если `compiland` был связан с ключом компоновщика/LTCG; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для версии 8.0|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)