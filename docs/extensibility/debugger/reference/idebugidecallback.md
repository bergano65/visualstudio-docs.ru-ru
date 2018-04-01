---
title: IDebugIDECallback | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f7f8991e361b46afe842cd65b933116d73bbfb69
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Позволяет вычислитель выражений (EE) отобразить сообщение в окне вывода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugIDECallback : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот обратный вызов реализуется Подсистема управляемой отладки.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Он может использоваться в вычислитель выражений для отправки выходных данных в окне вывода.  
  
## <a name="methods"></a>Методы  
 Этот интерфейс реализует следующий метод:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Отправляет указанное сообщение строку в окне вывода.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll