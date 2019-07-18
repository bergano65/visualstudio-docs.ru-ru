---
title: Функция SccBeginBatch | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6bb145358184117046e14b7b598ce6d4bb4586b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333889"
---
# <a name="sccbeginbatch-function"></a>Функция SccBeginBatch
Эта функция начинает пакетное последовательность операций системы управления версиями. [SccEndBatch](../extensibility/sccendbatch-function.md) будет вызываться, чтобы завершить работу пакета. Эти пакеты не могут быть вложенными.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Параметры
 Отсутствует.

## <a name="return-value"></a>Возвращаемое значение
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Пакет операций успешно начата.|
|SCC_E_UNKNOWNERROR|Обнаружена неспецифическая ошибка.|

## <a name="remarks"></a>Примечания
 Пакеты управления источника используются для выполнения одинаковых операций во всех несколько проектов или в нескольких контекстах. Пакеты можно использовать во избежание избыточных проекта диалоговым окнам от работы во время пакетной операции. `SccBeginBatch` Функции и [SccEndBatch](../extensibility/sccendbatch-function.md) используются как пара функций для определения начала и окончания операции. Они не могут быть вложенными. `SccBeginBatch` Задает флаг, указывающий, что пакетная операция выполняется.

 Пока действует пакетной операции, подключаемый модуль системы управления версиями следует не более одного диалогового окна для вопросов, пользователь получает и применить ответ в этом диалоговом окне для всех последующих операций.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)