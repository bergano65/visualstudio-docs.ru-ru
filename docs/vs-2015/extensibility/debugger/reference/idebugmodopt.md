---
title: IDebugModOpt | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e280e0b74d4cba3a988bccb5811a409c86c058b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571775"
---
# <a name="idebugmodopt"></a>IDebugModOpt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugModOpt](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmodopt).  
  
Представляет необязательный модификатор отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugModOpt : IUnknown  
```  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Полученный из [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объект, который представляет собой класс или метод.  
  
## <a name="methods"></a>Методы  
 Этот интерфейс реализует следующий метод:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Возвращает список необязательных модификаторов.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

