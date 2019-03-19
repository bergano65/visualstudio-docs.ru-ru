---
title: Интерфейс IProcessDebugManager | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d68c044cdc3d523841cc56814b8ca34bcd8aa037
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157247"
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