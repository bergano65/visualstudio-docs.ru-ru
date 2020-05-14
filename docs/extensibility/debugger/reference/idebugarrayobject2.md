---
title: IDebugArrayObject2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8a6580d0cbdead7866bbc6dd106a2aa0ea56f76
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736226"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Представляет объект управляемого массива и позволяет оценщику выражения (EE) определить базовый индекс (нижние границы) для массива.

## <a name="syntax"></a>Синтаксис

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Это реализовано управляемым движком отладки (DE).

## <a name="methods"></a>Методы
 В дополнение к методам интерфейса [IDebugArrayObject,](../../../extensibility/debugger/reference/idebugarrayobject.md) этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Извлекает базовые индексы (нижние границы) для каждого индекса с учетом количества измерений в массиве.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Определяет, определены ли в массиве базовые индексы (нижние границы).|

## <a name="remarks"></a>Примечания
 Оценщик выражения использует этот интерфейс для представления управляемых массивов в дереве разбора.

## <a name="requirements"></a>Требования
 Заголовок: Ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
