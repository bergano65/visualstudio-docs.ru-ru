---
title: Интерфейс IActiveScriptSiteDebugEx | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1e462630f7bf52c4ca94aa59df22616e9a335a7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345881"
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx — интерфейс
Реализуйте этот интерфейс, вместе с `IActiveScriptSiteDebug` интерфейс при создании узла, который должен получать уведомление об ошибке времени выполнения в приложении и при необходимости подключения к приложению для отладки. Диспетчер отладки процессов предоставляет уведомления через `IActiveScriptDebug` при отладчик сценариев Just-In-Time находится на компьютере. Если отладчик сценариев не Just-In-Time является найден, PDM обеспечивает уведомление через `IActiveScriptDebugEx` вместо этого.  
  
 Чтобы получить уведомление об ошибке времени выполнения, необходимо обрабатывать узла [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4). На основании действий пользователя, затем можно присоединить внутренний отладчик и возврата или возврата его запуск отладчика в OnScriptErrorDebug `pfEnterDebugger` параметра.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Информирует приложение о ошибки времени выполнения скрипта при процесс отладки Manager не удается найти во внешнем отладчике Just In Time.|