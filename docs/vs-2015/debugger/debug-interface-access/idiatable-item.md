---
title: 'Идиатабле:: Item | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6112a4580a68a98407723afab1ec3310d0f1cca9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62574805"
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
 окне Индекс записи таблицы в диапазоне от 0 до `count` -1, где `count` возвращается методом [идиатабле:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md).  
  
 `element`  
 заполняет Возвращает `IUnknown` объект, представляющий указанную запись таблицы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Таблица представляет коллекцию объектов. В зависимости от этих объектов параметр element может быть приведен к соответствующему интерфейсу. Например, если таблица содержит объекты [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , то параметр element может быть приведен к `IDiaSegment` интерфейсу.  
  
 Наиболее распространенным подходом является вызов `QueryInterface` метода в интерфейсе [идиатабле](../../debugger/debug-interface-access/idiatable.md) для соответствующего интерфейса перечислителя и использование методов перечислителя для доступа к содержимому таблицы. Пример см. в интерфейсе [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) .  
  
## <a name="see-also"></a>См. также:  
 [идиатабле](../../debugger/debug-interface-access/idiatable.md)   
 [Идиатабле:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
