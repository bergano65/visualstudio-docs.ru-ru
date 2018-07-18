---
title: Интерфейс IDebugHelper | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 3f0f70ecb8ead264d0d4b074f8fc1d9e3a6091eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727314"
---
# <a name="idebughelper-interface"></a>Интерфейс IDebugHelper
Служит в качестве фабрики для браузерах объектов и точек простого подключения. Диспетчер отладки процессов (PDM) реализует этот интерфейс, который используется обработчиков сценариев.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugHelper` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Возвращает свойства браузера, являющийся оболочкой для типа VARIANT.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Возвращает обозреватель свойств, который создает оболочку для типа VARIANT и обеспечивает пользовательские преобразования значений типа VARIANT или типов VARTYPE в строки.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Возвращает интерфейс событий, который создает оболочку для заданного `IDispatch` объекта.|