---
title: IDebugModOpt | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0477f8b3a39bd919a814828377228c5ccc02bd11
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmodopt"></a>IDebugModOpt
Представляет необязательный модификатор отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugModOpt : IUnknown  
```  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Получено из [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объект, представляющий класс или метод.  
  
## <a name="methods"></a>Методы  
 Этот интерфейс реализует следующий метод:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Получает список необязательных модификаторов.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll