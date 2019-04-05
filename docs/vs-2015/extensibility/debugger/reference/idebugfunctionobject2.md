---
title: IDebugFunctionObject2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9aa191d36c057e2d5cdcd1c551ac96f6804738b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993569"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Представляет функцию и улучшает [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейс.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugFunctionObject2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Вычислитель выражений (EE) реализует этот интерфейс, представляющий функцию.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Методы этого интерфейса отложить те **IDebugFunctionObject** одним из следующих способов:  
  
-   **IDebugEvaluate** метод принимает флаги.  
  
-   **CreateObject** метод принимает флаги и истечения времени ожидания.  
  
-   **CreateStringObjectWithLength** метод принимает длину.  
  
## <a name="methods"></a>Методы  
 Этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Создает объект, который использует конструктор параметров флаг вычисления и значение времени ожидания.|  
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Создает строковый объект, который имеет указанную длину.|  
|[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Вызывает функцию и возвращает результирующее значение как объект.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: EE.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
