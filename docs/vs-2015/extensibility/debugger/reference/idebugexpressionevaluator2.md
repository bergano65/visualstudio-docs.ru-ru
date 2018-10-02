---
title: IDebugExpressionEvaluator2 | Документация Майкрософт
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
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 741cedadd1897395326907179b99efa690603b6b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560146"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugExpressionEvaluator2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexpressionevaluator2).  
  
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Представляет улучшенная версия вычислитель выражений (EE).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется вычислитель выражений.  
  
## <a name="methods"></a>Методы  
 В дополнение к методам на [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) интерфейс, этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Извлекает объект службы по заданному идентификатору.|  
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Предварительно загружает модули, заданное поставщиком указанного символа.|  
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|Включает средство оценки выражений (EE) для указания интерфейс обратного вызова, который ядро отладки (DE) будет использовать для чтения настроек метрик.|  
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Задает путь к общеязыковой среды выполнения (CLR), загрузить в отладчик.|  
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Включает модуль отладки для передачи в обратный вызов средство оценки выражений во время инициализации.|  
|[Terminate](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Останавливает и удаляет средство оценки выражений.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

