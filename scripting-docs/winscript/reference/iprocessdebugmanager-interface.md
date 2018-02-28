---
title: "Интерфейс IProcessDebugManager | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IProcessDebugManager interface
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26c97fda6fc8657164e22d51eb041017a6239d98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanager-interface"></a>Интерфейс IProcessDebugManager
Основной интерфейс для диспетчера отладки процессов. Этот интерфейс можно создать, добавить или удалить виртуального приложения из процесса. Его можно перечислить кадры стека и потоки приложения.  
  
 Помимо методов, наследуемых от `IUnknown`, `IProcessDebugManager` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Создает новый объект приложения отладки для этого приложения.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Возвращает объект приложения по умолчанию для текущего процесса.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Добавляет приложение в список диспетчера отладки компьютера запущенные приложения.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Удаляет приложение с запуском список приложений.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Создает новый вспомогательный документ отладки для этого приложения.|