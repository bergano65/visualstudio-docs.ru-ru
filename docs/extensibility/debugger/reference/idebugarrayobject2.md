---
title: IDebugArrayObject2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb66f52cc6fb5e9dfd370f45388218b3eda34eb5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414155"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

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
 Заголовок: EE.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll