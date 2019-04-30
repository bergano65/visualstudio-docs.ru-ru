---
title: Интерфейс IRemoteDebugApplication110 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110 Interface
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea8f3f983cf7279cf6dc9600813a08268cef8301
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383496"
---
# <a name="iremotedebugapplication110-interface"></a>IRemoteDebugApplication110 — интерфейс
Используется для предоставления новых возможностей, которые могут быть вызваны отладчиках скриптов и вызывающих объектов в процессе.  
  
> [!IMPORTANT]
> Этот интерфейс реализуется в PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Интерфейс `IRemoteDebugApplication110` предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|Вызывается для обновления параметров отладчика. Параметры по умолчанию 0 (SDO_NONE).|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|Возвращает текущий набор доступных параметров.|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|Возвращает основной поток для узлов, которые вызывают SetSite.|