---
title: IDiaLineNumber::get_compiland | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_compiland method
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f1484a79731d9e38b2ad2fe7eb2a716680f0161
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idialinenumbergetcompiland"></a>IDiaLineNumber::get_compiland
Извлекает ссылку на символ компилируемого объекта вызвал байты текст изображения.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_compiland (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pRetVal  
 [out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект для компилируемого объекта вызвал байты текст изображения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)