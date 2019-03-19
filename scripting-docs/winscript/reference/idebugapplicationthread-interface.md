---
title: Интерфейс IDebugApplicationThread | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread interface
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a464085eddbea4f5d29c684c0f1dabc6f853b6d1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158793"
---
# <a name="idebugapplicationthread-interface"></a>Интерфейс IDebugApplicationThread
Позволяет модулям языка и узлам обеспечивать синхронизацию потоков и поддерживать сведения о состоянии конкретного потока отладки. Этот интерфейс расширяет `IRemoteDebugApplicationThread` интерфейс для предоставления без удаленного доступа к потоку.  
  
 Помимо методов, наследуемых от `IRemoteDebugApplicationThread`, `IDebugApplicationThread` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Предоставляет механизм для вызывающего объекта для выполнения кода в потоке приложения.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Определяет, является ли этот поток текущим выполняемым потоком.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Определяет, является ли этот поток в поток отладки.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Задает описание для данного потока.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Задает описание состояние потока.|