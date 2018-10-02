---
title: IDiaEnumTables::Item | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea80cbcda60b54f17e79e492c43058579465ad90
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568577"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaEnumTables::Item](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumtables-item).  
  
Возвращает таблицу с помощью индекса или имени.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `index`  
 [in] Индекс или имя [IDiaTable](../../debugger/debug-interface-access/idiatable.md) требуется получить. Если используется вариант целое число, он должен быть в диапазоне от 0 до `count`-1, где `count` как возвращаемый [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) метод.  
  
 `table`  
 [out] Возвращает [IDiaTable](../../debugger/debug-interface-access/idiatable.md) объект, представляющий нужную таблицу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если указан вариант строка, строка имен конкретной таблицы. Имя должно быть одно из имен таблицы как определено в [константы (SDK отладки интерфейса доступа)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## <a name="example"></a>Пример  
  
```cpp#  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Константы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)



