---
title: Интерфейс Искриптскриптлет | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptScriptlet interface
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7973aee209695592f022d0e05a770caa1e694c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571886"
---
# <a name="iscriptscriptlet-interface"></a>Интерфейс IScriptScriptlet
Объект, реализующий интерфейс `IScriptScriptlet`, представляет скрипт обработчика событий.  
  
 В дополнение к методам, унаследованным от `IScriptEntry`, интерфейс `IScriptScriptlet` предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Возвращает имя события, связанного с скриптлет.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Возвращает простое имя события, связанное с скриптлет. Это имя состоит из одного слова, которое не содержит пробелов.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Возвращает последний идентификатор в полном имени узла объекта скриптлет.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Задает имя события, связанного с скриптлет.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Задает простое имя события, связанное с скриптлет. Это имя состоит из одного слова, которое не содержит пробелов.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Задает последний идентификатор в полном имени узла объекта скриптлет.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы для создания активных скриптов](../../winscript/reference/active-script-authoring-interfaces.md)