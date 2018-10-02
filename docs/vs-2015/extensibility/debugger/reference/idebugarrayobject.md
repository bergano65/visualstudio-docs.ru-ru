---
title: IDebugArrayObject | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 02d8c9758dc12a5f19f489d1221446bd4b855c96
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572215"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugArrayObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugarrayobject).  
  
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс представляет объект массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений реализует этот интерфейс для представления массива.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейса можно получить этот интерфейс, используя [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) Если объект представляет собой массив.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам на `IDebugObject` интерфейс, следующие методы реализуются на `IDebugArrayObject` интерфейс.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Получает число элементов в массиве.|  
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Получает элемент массива.|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Получает все элементы массива.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Возвращает ранг массива.|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Возвращает размерность массива.|  
  
## <a name="remarks"></a>Примечания  
 Вычислитель выражений использует этот интерфейс для представления массивов в дерево синтаксического анализа.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

