---
title: Интерфейс IActiveScriptSiteDebug32 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 2a55161f76fcd98b52ddb769c640aca0e903239b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835268"
---
# <a name="iactivescriptsitedebug32-interface"></a>Интерфейс IActiveScriptSiteDebug32
Интеллектуальные узлы реализуют `IActiveScriptSiteDebug32` интерфейс для управления документами и для участия в отладке. `IActiveScriptSite`Объект обычно предоставляет реализацию `IActiveScriptSiteDebug32` интерфейса. Если это сделано, вызовите `IActiveScriptSite::QueryInterface` метод, чтобы получить `IActiveScriptSiteDebug32` интерфейс.  
  
 В дополнение к методам, унаследованным от `IUnknown` , `IActiveScriptSiteDebug32` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Возвращает объект приложения отладки, связанный с этим сайтом скриптов.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Используется обработчиком языка для делегирования `IDebugCodeContext::GetSourceContext` .|