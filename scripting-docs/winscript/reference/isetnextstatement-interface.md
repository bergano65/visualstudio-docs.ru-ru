---
title: "Интерфейс ISetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Интерфейс ISetNextStatement
Этот интерфейс реализуется переводчиком, чтобы включить диспетчер процесса отладки для обновления текущей оператор.  Он реализуется из объекта кадра стека и PDM получает этот интерфейс с помощью QueryInterface.  
  
 интерфейс содержит методы, которые полезны для размещения точки выполнения, который определяет следующую выписку для выполнения.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `ISetNextStatement` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Определяет, находится ли точка выполнения можно установить в указанное расположение.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Установка точки выполнения в указанное место.|