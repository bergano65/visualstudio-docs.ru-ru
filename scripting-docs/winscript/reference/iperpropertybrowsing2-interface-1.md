---
title: Интерфейс IPerPropertyBrowsing2 1 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bded7159b72fc8c1ae8408611ce858105e6734da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344043"
---
# <a name="iperpropertybrowsing2-interface-1"></a>Интерфейс IPerPropertyBrowsing2 1
Обращается к сведения на страницах свойств, предлагаемых объекта.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|`GetDisplayString`|Возвращает текстовую строку, описывающую указанного свойства.|  
|`MapPropertyToPage`|Возвращает идентификатор CLSID страницы свойств, позволяющая управлять указанное свойство.|  
|`GetPredefinedStrings`|Возвращает сосчитанный массив строк (`LPOLESTR` указатели) списков описаний допустимых значений, которые может принять указанное свойство.|  
|`SetPredefinedValue`|Задает значение свойства с предопределенным значением, определенный токеном `dwCookie.`|  
  
## <a name="requirements"></a>Требования  
 Заголовок: dbgprop.h