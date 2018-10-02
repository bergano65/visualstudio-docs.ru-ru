---
title: IDebugArrayObject2 | Документация Майкрософт
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
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de10cd047de173440661201f8daaf9a7630612c6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568740"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugArrayObject2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugarrayobject2).  
  
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Представляет объект управляемого массива и позволяет вычислитель выражений (EE), чтобы определить базовый индекс (нижней границы) для массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugArrayObject2 : IDebugArrayObject  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Это реализуется путем Подсистема управляемой отладки (DE).  
  
## <a name="methods"></a>Методы  
 В дополнение к методам на [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) интерфейс, этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Получает базовый индексы (нижней границы) для каждого индекса, учитывая количество измерений в массиве.|  
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Определяет, имеет ли массив базовые индексы (нижних границ) определен.|  
  
## <a name="remarks"></a>Примечания  
 Вычислитель выражений использует этот интерфейс для представления управляемых массивов в дерево синтаксического анализа.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

