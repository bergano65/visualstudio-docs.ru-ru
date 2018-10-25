---
title: Интерфейс IActiveScriptDebug | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0e21f4c99da886bc4907acf8b0934e1b46d57689
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942092"
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