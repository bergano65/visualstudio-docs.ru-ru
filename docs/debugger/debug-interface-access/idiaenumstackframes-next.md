---
title: IDiaEnumStackFrames::Next | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac6fa3d146cb7efa86d24ff66821c46e64b4641b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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