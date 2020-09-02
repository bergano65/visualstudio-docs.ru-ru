---
title: 'IDiaEnumTables:: Item | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9eec94a5a02eda8fe9b1b3bf8f76f5050ab1e020
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423872"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает таблицу с помощью индекса или имени.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `index`  
 окне Индекс или имя извлекаемого объекта [идиатабле](../../debugger/debug-interface-access/idiatable.md) . Если используется целочисленный вариант, он должен находиться в диапазоне от 0 до `count` -1, где `count` является возвращаемым методом [IDiaEnumTables:: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) .  
  
 `table`  
 заполняет Возвращает объект [идиатабле](../../debugger/debug-interface-access/idiatable.md) , представляющий нужную таблицу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Если указан строковый вариант, то строка будет указывать на конкретную таблицу. Имя должно быть одним из имен таблиц, как определено в [константах (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## <a name="example"></a>Пример  
  
```cpp#  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>См. также:  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [идиатабле](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables:: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Константы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)
