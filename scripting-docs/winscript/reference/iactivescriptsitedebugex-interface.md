---
title: "Iactivescriptsitedebugex — интерфейс | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cf5849ff1fca282bace97774c6b7ac9e4510226
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx — интерфейс
Реализуйте этот интерфейс вместе с `IActiveScriptSiteDebug` интерфейс при создании узла, который необходимо получить уведомление об ошибке времени выполнения в приложении и при необходимости присоедините к приложению для отладки. Диспетчер отладки процессов обеспечивает уведомление через `IActiveScriptDebug` при отладчик сценариев непосредственно в момент находится на компьютере. Если отладчик сценариев не только время будет найден, PDM обеспечивает уведомление через `IActiveScriptDebugEx` вместо него.  
  
 Чтобы получить уведомление об ошибке времени выполнения, необходимо обрабатывать узла [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4). На основании действий пользователя, затем можно присоединить отладчик внутренних и возврата или возвратить запуск отладчика в OnScriptErrorDebug `pfEnterDebugger` параметра.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Информирует приложение о ошибку во время выполнения сценария при диспетчера отладки процесса не удается найти внешнем только раз в отладчике.|