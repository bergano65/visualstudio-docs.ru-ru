---
title: IDiaAddressMap | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb1593f59125c4b6325bfd97015485cc2a4d85f6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468974"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Предоставляет управление как пакет SDK для рассчитывает виртуального и относительные виртуальные адреса для отладки объектов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaAddressMap`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Указывает, установлен ли Карта адресов для конкретного сеанса.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Указывает, следует ли использовать для преобразования символа адресов Карта адресов.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Указывает, включен ли вычисления и использования относительными виртуальными адресами.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Позволяет клиенту включить или отключить расчет относительными виртуальными адресами.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Извлекает текущее выравнивание изображения.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Задает выравнивание изображения.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Задает изображения, заголовки, чтобы включить трансляцию относительными виртуальными адресами.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Предоставляет адрес сопоставляются поддерживают переводы макета изображения.|  
  
## <a name="remarks"></a>Примечания  
 Элемент управления, предоставляемый данным интерфейсом, содержащийся в двух наборов данных, указывается: изображения, заголовки и устраните карты. Большинство клиентов используйте [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод для поиска правильной отладочную информацию для образа и метод может обычно обнаруживать все необходимые заголовки и карты самих данных. Однако некоторые клиенты реализовать специализированные обработки и для поиска данных. Такие клиенты используют методы `IDiaAddressMap` интерфейс для предоставления пакет SDK для результатов поиска.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс доступен из объекта сеанса доступа к интерфейсу отладки. Клиент вызывает метод `QueryInterface` метод для доступа к интерфейсу отладки объекта интерфейс сеанса, обычно [IDiaSession](../../debugger/debug-interface-access/idiasession.md), чтобы получить `IDiaAddressMap` интерфейса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)