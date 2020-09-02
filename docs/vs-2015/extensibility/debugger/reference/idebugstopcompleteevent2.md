---
title: IDebugStopCompleteEvent2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2a6a6e69bf47751706710801dd78c832ccd2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546927"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Модуль отладки (DE) может отправить это необязательное событие в Диспетчер отладки сеансов (SDM) при остановке программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Это новый интерфейс для [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] . Предыдущие выпуски не поддерживали асинхронную остановку.  
  
 Метод " [останавливает](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) " вызывается SDM в многопроцессных или многопрограммных сценариях. Когда одна программа отправляет событие остановки в SDM, SDM запрашивает остановку других программ.  
  
 Он используется для асинхронного информирования SDM о том, что программа остановлена. Это полезно для модуля отладки интерпретатора, где иногда нет кода, выполняющегося в отлаживаемой программе [, поэтому не удается выполнить завершение](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) синхронно. Если модуль отладки хочет применить это асинхронное уведомление, он должен возвратить `S_ASYNC_STOP` из " [останавливается](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)".  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
