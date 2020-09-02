---
title: IDiaAddressMap | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 012d6b1ca06b06f56239048fee712d898a79efa9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547511"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Предоставляет контроль над тем, как пакет SDK DIA рассчитывает виртуальные и относительные виртуальные адреса для объектов отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaAddressMap` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Указывает, была ли установлена схема адресов для конкретного сеанса.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Указывает, следует ли использовать карту адресов для преобразования адресов символов.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Указывает, включен ли расчет и использование относительных виртуальных адресов.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Позволяет клиенту включать или отключать Вычисление относительных виртуальных адресов.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Извлекает текущее выравнивание изображения.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Задает выравнивание изображения.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Задает заголовки изображений, чтобы включить перевод относительных виртуальных адресов.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Предоставляет карту адресов для поддержки перевода макета изображения.|  
  
## <a name="remarks"></a>Remarks  
 Элемент управления, предоставляемый этим интерфейсом, инкапсулируется в два набора данных: заголовки изображений и карты адресов. Большинство клиентов используют метод [идиадатасаурце:: лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) для поиска правильных отладочных данных для изображения, и метод обычно обнаруживает все необходимые заголовки и сопоставляет данные. Однако некоторые клиенты реализуют специализированную обработку и поиск данных. Такие клиенты используют методы `IDiaAddressMap` интерфейса для предоставления пакета SDK Dia с результатами поиска.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс доступен из объекта сеанса DIA. Клиент вызывает `QueryInterface` метод в интерфейсе объекта сеанса DIA, обычно [IDiaSession](../../debugger/debug-interface-access/idiasession.md), для получения `IDiaAddressMap` интерфейса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2. h  
  
 Библиотека: диагуидс. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Идиадатасаурце:: Лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
