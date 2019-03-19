---
title: Интерфейс IPerPropertyBrowsing2 1 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 156cf9a1e104b8a2d7ffe4e48bd39642ef1abbd0
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159586"
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