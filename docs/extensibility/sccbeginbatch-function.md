---
title: Функция Сккбегинбатч | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c7982d8c8c0d71f8c79e9b808be5453d384882d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701200"
---
# <a name="sccbeginbatch-function"></a>Функция Сккбегинбатч
Эта функция запускает пакетную последовательность операций системы управления версиями. Для завершения пакета будет вызван [скцендбатч](../extensibility/sccendbatch-function.md) . Эти пакеты не могут быть вложенными.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Параметры
 Нет.

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Пакетная операция успешно началась.|
|SCC_E_UNKNOWNERROR|Неконкретный сбой.|

## <a name="remarks"></a>Remarks
 Пакеты управления версиями используются для выполнения одних и тех же операций в нескольких проектах или нескольких контекстах. Пакеты можно использовать для исключения избыточных диалоговых окон для отдельных проектов из процесса выполнения пакетной операции. `SccBeginBatch`Функция и [скцендбатч](../extensibility/sccendbatch-function.md) используются в качестве пары функций для указания начала и конца операции. Они не могут быть вложенными. `SccBeginBatch` задает флаг, указывающий, что выполняется пакетная операция.

 Во время выполнения пакетной операции подключаемый модуль системы управления версиями должен представлять максимум одно диалоговое окно для любого вопроса пользователя и применять ответ от этого диалогового окна во всех последующих операциях.

## <a name="see-also"></a>См. также раздел
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
