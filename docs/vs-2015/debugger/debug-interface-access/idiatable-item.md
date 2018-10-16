---
title: IDiaTable::Item | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30b2de7590a20c3d0b9e1ec911779d407a46b1f6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289124"
---
# <a name="idiatableitem"></a>IDiaTable::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает ссылку на указанную запись в таблице.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `index`  
 [in] Индекс записи в таблице в диапазоне от 0 до `count`-1, где `count` возвращается [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)метод.  
  
 `element`  
 [out] Возвращает `IUnknown` , представляющий элемент указанной таблицы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Таблицы представляет коллекцию объектов. В зависимости от объектов элемент можно привести на соответствующий интерфейс. Например, если таблица содержит [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) объектов, а затем элемент параметра может быть приведен к `IDiaSegment` интерфейс.  
  
 Это наиболее распространенный подход для вызова `QueryInterface` метод в [IDiaTable](../../debugger/debug-interface-access/idiatable.md) интерфейса для интерфейса соответствующим перечислителем и использовать конкретные методы перечислителя для доступа к содержимому таблицы. См. в разделе [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) интерфейс пример.  
  
## <a name="see-also"></a>См. также  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)



