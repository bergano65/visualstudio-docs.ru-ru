---
title: "IDebugApplicationNode100 — интерфейс | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100 — интерфейс"
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100 — интерфейс
Интерфейс `IDebugApplicationNode100` расширяющий функциональность [Интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md).  Можно получить экземпляр этого интерфейса путем вызова QueryInterface для реализации [Интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
>  Этот интерфейс реализуется PDM v10.0 и большим.  Обнаружен в activdbg100.h.  
  
## Методы  
 Интерфейс `IDebugApplicationNode100` предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Возвращает текстовые документы, скрыватьы указанным фильтром.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Определяет, принадлежит ли указанный документ на один из дочерних узлов данного узла.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Устанавливает фильтр для указанной реализации [Интерфейс IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md).  Она позволяет отладчики скрипта, чтобы отфильтровать компилятор\- приложения, созданные узлы дочернего элемента так как PDM больше не отправляет события при создатьы или удалитьы узлы.  По умолчанию все узлы будут отправитьо.|