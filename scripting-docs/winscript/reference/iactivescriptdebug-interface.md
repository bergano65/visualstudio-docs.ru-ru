---
title: Интерфейс IActiveScriptDebug | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6341b5c3763d6e4c836b3bdc0539552fcbe7f980
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955033"
---
# <a name="iactivescriptdebug-interface"></a>Интерфейс IActiveScriptDebug
Реализуется обработчиков сценариев, поддерживающие отладку. Как правило, объект, реализующий `IActiveScriptDebug` также интерфейс реализует `IActiveScript` интерфейс. Если это так, вызовите `IActiveScript::QueryInterface` метод, чтобы получить `IActiveScriptDebug` интерфейс.  
  
 `IActiveScriptDebug` Интерфейс предоставляет средства для:  
  
- Промежуточные узлы на управление документа.  
  
- Диспетчер отладки процессов для синхронизации, отладку нескольких обработчиков сценариев.  
  
  Помимо методов, наследуемых от `IUnknown`, `IActiveScriptDebug` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Возвращает атрибуты текста для произвольный блок текста сценария.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Возвращает атрибуты текста для произвольных скриптлета.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Делегирует `IDebugDocumentContext::EnumCodeContexts`.|