---
title: Идебугобжект | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c179a4443c23373fb92adf522ee0af34acb19c3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695271"
---
# <a name="idebugobject"></a>IDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс представляет объект, создаваемый связывателем для инкапсуляции значений символов и выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugObject : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений реализует этот интерфейс для представления объекта.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс является базовым классом для всех объектов, которые средство оценки выражений использует в проанализированных выражениях. Он возвращается вызовом метода [BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md) . [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) получает более специализированные интерфейсы из этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugObject` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Возвращает размер объекта.|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Возвращает значение объекта в виде последовательности байтов.|  
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Задает значение объекта из последовательности байтов.|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Задает значение ссылки для этого объекта.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Возвращает контекст памяти, представляющий адрес значения объекта.|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Создает копию управляемого объекта в адресном пространстве модуля отладки.|  
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Проверяет, является ли этот объект пустой ссылкой.|  
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Сравнивает объект с данным.|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Определяет, доступен ли этот объект только для чтения.|  
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Определяет, является ли объект прозрачным прокси-сервером.|  
  
## <a name="remarks"></a>Remarks  
 Средство оценки выражений использует этот интерфейс в качестве базового класса для представления объектов в дереве синтаксического анализа.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы оценки выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)   
 [Выполняется](../../../extensibility/debugger/reference/idebugbinder-bind.md)
