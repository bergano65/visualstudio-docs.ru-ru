---
title: "IRemoteDebugApplication110 — интерфейс | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110 — интерфейс"
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IRemoteDebugApplication110 — интерфейс
Используемый, чтобы предоставить новые возможности, которые могут быть Позвонитьы отладчиками скрипта и вызывающими объектами в процессе.  
  
> [!IMPORTANT]
>  Этот интерфейс реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Методы  
 Интерфейс `IRemoteDebugApplication110` предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|Вызываемый для обновления параметров отладчика.  Параметры имеют значение по умолчанию равно 0 \(SDO\_NONE\).|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|Возвращает текущий набор параметров, которые включены.|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|Возвращает основной поток для узлов, которые вызывают метод SetSite.|