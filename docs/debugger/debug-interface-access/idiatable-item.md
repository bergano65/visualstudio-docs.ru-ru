---
title: IDiaTable::Item | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd734d287a4740a25840d93b4724b45396c7dd87
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470079"
---
# <a name="idiatableitem"></a>IDiaTable::Item
Извлекает ссылку на указанную запись в таблице.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `index`  
 [in] Индекс записи в таблице, в диапазоне от 0 до `count`-1, где `count` возвращается [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)метод.  
  
 `element`  
 [out] Возвращает `IUnknown` , представляющий запись указанной таблицы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Таблицы представляет коллекцию объектов. В зависимости от этих объектов параметра элемента может быть приведен к соответствующий интерфейс. Например, если таблица содержит [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) объектов, а затем элемент параметра может быть приведен к `IDiaSegment` интерфейса.  
  
 Это наиболее распространенный подход для вызова `QueryInterface` метод в [IDiaTable](../../debugger/debug-interface-access/idiatable.md) интерфейса для интерфейса соответствующим перечислителем и использования перечислителя конкретных методов для доступа к содержимому таблицы. В разделе [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) интерфейса в качестве примера.  
  
## <a name="see-also"></a>См. также  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)