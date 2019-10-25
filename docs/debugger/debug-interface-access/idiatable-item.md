---
title: 'Идиатабле:: Item | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d402f5ad54d5c0f487cebb3a8c53f68d17828ed4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738715"
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

окне Индекс записи таблицы в диапазоне от 0 до `count`-1, где `count` возвращается методом [идиатабле:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md).

 `element`

заполняет Возвращает объект `IUnknown`, представляющий указанную запись таблицы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Таблица представляет коллекцию объектов. В зависимости от этих объектов параметр element может быть приведен к соответствующему интерфейсу. Например, если таблица содержит объекты [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , то параметр element может быть приведен к интерфейсу `IDiaSegment`.

 Это более распространенный подход к вызову метода `QueryInterface` в интерфейсе [идиатабле](../../debugger/debug-interface-access/idiatable.md) для соответствующего интерфейса перечислителя и использования для доступа к содержимому таблицы конкретных методов перечислителя. Пример см. в интерфейсе [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) .

## <a name="see-also"></a>См. также
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)