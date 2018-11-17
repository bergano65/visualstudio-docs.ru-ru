---
title: IDebugArrayField | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ef60550dcea362fd196ba2740d7347981a6d01bb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745634"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс описывает символ массива или типа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugArrayField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Поставщик символов реализует этот интерфейс на тот же объект, реализующий [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейс. Этот интерфейс является специализацией, которая представляет массив объектов.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Используйте [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для получения этого интерфейса из [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейс, если [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) Возвращает флаг `FIELD_TYPE_ARRAY`.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам на [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) и [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейсы, этот интерфейс реализует следующее:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Возвращает количество элементов в массиве.|  
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Получает тип элемента в массиве.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Возвращает ранг массива.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

