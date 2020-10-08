---
title: 'IDiaSymbol:: get_isMSILNetmodule | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isMSILNetmodule method
ms.assetid: 593827f3-8437-4a12-ada4-ff715ec95fb2
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 75b4917d7678859e310d422be0279f733a25cfcb
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "91838210"
---
# <a name="idiasymbolget_ismsilnetmodule"></a>IDiaSymbol::get_isMSILNetmodule
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает флаг, указывающий, является ли модуль NETMODULE (модуль MSIL, который содержит только метаданные без машинных символов).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_isMSILNetmodule(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pFlag`  
 заполняет Возвращает `TRUE` , если модуль является MSIL; в противном случае возвращает `FALSE` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Комментарии  
 Это свойство доступно из `SymTagCompilandDetails` типа символов (см. [компиланддетаилс](../../debugger/debug-interface-access/compilanddetails.md)).  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2. h|  
|Версия:|Пакет SDK для DIA v 8.0|  
  
## <a name="see-also"></a>См. также:  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)
