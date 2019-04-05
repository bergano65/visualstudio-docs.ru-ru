---
title: IDiaSymbol::get_typeIds | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1d2a97f9c71a78a16d5763e26f09241ae916a79f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979420"
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает массив значений типа специфичные для компилятора идентификатор для этого символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cTypeIds`  
 [in] Размер буфера для хранения данных.  
  
 `pcTypeIds`  
 [out] Возвращает количество `typeIds` записаны, или, если `typeIds` является `NULL`, затем общее число доступных идентификаторов типов.  
  
 `typeIds[]`  
 [out] Массив, заполненный идентификаторы типа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
