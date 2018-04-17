---
title: IDiaSymbol::get_types | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7340e7b0c3512c8a453dc9af8cc9915235a425be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
Извлекает массив типов компилятора для этого символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cTypes`  
 [in] Размер буфера для хранения данных.  
  
 `pcTypes`  
 [out] Возвращает количество типов записи, или если `types` параметр `NULL`, затем общее число доступных типов.  
  
 `types[]`  
 [out] Массив, который должен быть заполнен с [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объекты, представляющие все типы для этого символа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает свойство недоступно для символа.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)