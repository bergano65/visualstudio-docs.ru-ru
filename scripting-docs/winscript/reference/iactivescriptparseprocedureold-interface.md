---
title: "Интерфейс IActiveScriptParseProcedureOld | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedureOld
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedureOld — интерфейс"
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IActiveScriptParseProcedureOld
Разрешает текст исходного кода для процедур, добавляемый к скрипту.  Для интерпретированных языков скриптов, не имеющих независимую среды разработки, такими как VBScript, это обеспечивает альтернативный механизм \(за исключением `IActiveScriptParse` или `IPersist*`\) чтобы добавить процедуры сценария в пространстве имен.  
  
> [!NOTE]
>  Этот интерфейс нерекомендуем в использование интерфейса `IActiveScriptParseProcedure`.  
  
## Методы  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IActiveScriptParseProcedureOld` предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Анализирует заданную процедура кода и добавляет процедуры в пространстве имен.|  
  
## См. также  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)