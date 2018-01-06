---
title: "IDiaTable::Item | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 12d04da8ea2c2a136b61924578fcb925b17fc12f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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