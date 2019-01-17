---
title: Интерфейс IActiveScriptSiteDebug32 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e7937311e01274570e34bd639a0dc5f68206a3aa
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345569"
---
# <a name="iactivescriptsitedebug32-interface"></a>Интерфейс IActiveScriptSiteDebug32
Реализовать промежуточных узлов `IActiveScriptSiteDebug32` интерфейс для выполнения управления документами и участвовать в отладке. `IActiveScriptSite` Объект обычно содержит реализацию `IActiveScriptSiteDebug32` интерфейс. Если это сделано, вызовите `IActiveScriptSite::QueryInterface` метод, чтобы получить `IActiveScriptSiteDebug32` интерфейс.  
  
 Помимо методов, наследуемых от `IUnknown`, `IActiveScriptSiteDebug32` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Возвращает объект отладки приложения, связанные с этим сайтом скрипта.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Используемый модуль языка делегировать `IDebugCodeContext::GetSourceContext`.|