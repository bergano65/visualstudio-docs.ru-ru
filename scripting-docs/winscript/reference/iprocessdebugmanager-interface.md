---
title: Интерфейс IProcessDebugManager | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProcessDebugManager interface
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5feb67b1a616eeaa855b27cb12ea9b3146545ebd
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345127"
---
# <a name="iprocessdebugmanager-interface"></a>Интерфейс IProcessDebugManager
Основной интерфейс для диспетчера отладки процессов. Этот интерфейс может создать, добавить или удалить виртуальное приложение в процессе. Его можно перечислить кадров стека и потоки приложения.  
  
 Помимо методов, наследуемых от `IUnknown`, `IProcessDebugManager` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Создает новый объект отладки приложения для этого приложения.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Возвращает объект приложения по умолчанию для текущего процесса.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Добавляет приложение диспетчера отладки компьютера список выполняемых приложений.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Удаляет приложение из выполняемого список приложений.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Создает новый документ вспомогательное средство отладки для этого приложения.|