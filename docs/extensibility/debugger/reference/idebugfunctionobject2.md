---
title: IDebugFunctionObject2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bbf52230b93357e85326f868254cf1d5c5a9dbb9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Представляет функцию и повышает [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugFunctionObject2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Вычислитель выражений (Эстония) реализует этот интерфейс для представления функции.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Методы этого интерфейса отложить биты **IDebugFunctionObject** одним из следующих способов:  
  
-   **IDebugEvaluate** метод принимает флаги.  
  
-   **CreateObject** метод принимает флаги и истечения времени ожидания.  
  
-   **CreateStringObjectWithLength** метод принимает длиной.  
  
## <a name="methods"></a>Методы  
 Этот интерфейс реализует следующие методы:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Создает объект, который использует конструктор заданы параметры флаг оценки, а также значение времени ожидания.|  
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Создает объект string, имеющего указанную длину.|  
|[Оценка](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Вызывает функцию и возвращает результирующее значение в виде объекта.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll