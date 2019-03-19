---
title: Интерфейс IDebugHelper | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1708b742a484a2e7d6d48cf759f15c08711e13d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148064"
---
# <a name="idebughelper-interface"></a>Интерфейс IDebugHelper
Служит в качестве фабрики для обозревателей объектов и простых точек подключения. Диспетчер отладки процессов (PDM) реализует этот интерфейс, который используются обработчиками скриптов.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugHelper` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Возвращает браузер свойств, который создает оболочку для типа VARIANT.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Возвращает браузер свойств, который заключает в оболочку типа VARIANT и позволяет выполнять пользовательские преобразование значениями VARIANT или типами VARTYPE в строки.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Возвращает интерфейс событий, который создает оболочку для заданного `IDispatch` объекта.|