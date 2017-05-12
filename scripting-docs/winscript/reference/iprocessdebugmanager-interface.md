---
title: "Интерфейс IProcessDebugManager | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IProcessDebugManager — интерфейс"
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IProcessDebugManager
Основной интерфейс для процесса отладки диспетчер.  Этот интерфейс может создать, добавить или удалить виртуальное приложение из процесса.  Он может перечислить кадры стека и потоки приложения.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IProcessDebugManager` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Создает новый объект отладки приложения для данного приложения.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Возвращает объект по умолчанию приложения для текущего процесса.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Добавляет приложение на компьютер отладка список диспетчера выполняющихся приложений.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Удаляет приложение из выполняющегося списка приложения.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Создает новую отладка вспомогательный объект документа для данного приложения.|