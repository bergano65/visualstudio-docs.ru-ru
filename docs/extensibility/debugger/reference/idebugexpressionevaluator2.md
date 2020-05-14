---
title: IDebugExpressionО-оценщик2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7041456bf0f3ae7930a73399d43dbf7cac6b3b32
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729138"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Представляет собой расширенную версию оценщика выражения (EE).

## <a name="syntax"></a>Синтаксис

```
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Этот интерфейс реализован оценщиком выражения.

## <a name="methods"></a>Методы
 В дополнение к методам на интерфейсе [IDebugExpressionEvaluator,](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Извлекает объект обслуживания с учетом его уникального идентификатора.|
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Предзагружает модули, назначенные указанным поставщиком символов.|
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|Позволяет оценщику выражения (EE) указать интерфейс обратного вызова, который будет использовать для чтения параметров метрики.|
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Устанавливает путь к общему времени выполнения языка (CLR), загруженным в отладчик.|
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Позволяет отладке двигателя передать обратный вызов оценщику выражения во время инициализации.|
|[Завершить](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Останавливает и очищает оценщика выражения.|

## <a name="requirements"></a>Требования
 Заголовок: Ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
