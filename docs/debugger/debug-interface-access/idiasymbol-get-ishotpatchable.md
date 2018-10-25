---
title: IDiaSymbol::get_isHotpatchable | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isHotpatchable method
ms.assetid: b7b6f490-1cf2-4a68-9237-b152dac84d3c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 53e125db7928c71c6f1cc6b2cab04e3612a87ef9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834894"
---
# <a name="idiasymbolgetishotpatchable"></a>IDiaSymbol::get_isHotpatchable
Получает флаг, указывающий, является ли модуль был скомпилирован с помощью [/hotpatch (создать образ с обновлениями)](/cpp/build/reference/hotpatch-create-hotpatchable-image) параметр компилятора.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_isHotpatchable(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pFlag`  
 [out] Возвращает `TRUE` при-исправлять; в противном случае модуль возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Это свойство доступно из `SymTagCompilandDetails` символ типа (см. в разделе [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)).  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для версии 8.0|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)