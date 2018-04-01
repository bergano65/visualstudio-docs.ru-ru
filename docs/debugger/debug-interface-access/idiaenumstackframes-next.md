---
title: IDiaEnumStackFrames::Next | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8bfdf9e71bfb13c9f8cc730a33ecb2813e117e5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Извлекает указанное число элементов кадра стека из последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 [in] Число элементов stackframe перечислителя, который требуется получить.  
  
 rgelt  
 [out] Массив, который должен быть заполнен с требуемым [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) объектов.  
  
 pceltFetched  
 [out] Возвращает количество стека элементы-фреймы извлеченных перечислителя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если отсутствуют дополнительные кадры стека. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)