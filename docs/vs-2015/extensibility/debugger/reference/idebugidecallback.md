---
title: IDebugIDECallback | Документация Майкрософт
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
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec4e3fee021b02c80b47635d4872ec1bf51e0cc9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557755"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugIDECallback](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugidecallback).  
  
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Позволяет вычислитель выражений (EE) для отображения сообщения в окне вывода отладчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugIDECallback : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот обратный вызов реализуется Подсистема управляемой отладки.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Он может использоваться в вычислитель выражений для отправки выходных данных в окне вывода отладчика.  
  
## <a name="methods"></a>Методы  
 Этот интерфейс реализует следующий метод:  
  
|Метод|Описание|  
|------------|-----------------|  
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Отправляет заданной строкой сообщения в окне вывода отладчика.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

