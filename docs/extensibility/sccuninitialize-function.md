---
title: Функция SccUninitialize | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f71e34352150143c7db207ed31ea6e879f97ca18
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338497"
---
# <a name="sccuninitialize-function"></a>Функция SccUninitialize
Эта функция очищает все выделения или открытых подключений, созданных предыдущим вызовом [SccInitialize](../extensibility/sccinitialize-function.md) в ожидании завершения работы подключаемого модуля системы управления версиями.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Параметры
 pvContext

[in] Указатель на структуру исходного элемента управления контекста подключаемый модуль создан в [SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Возвращаемое значение
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Очистка завершена успешно.|

## <a name="remarks"></a>Примечания
 Подключаемый модуль системы управления версиями ответственность за освобождение памяти, выделенной подключаемый модуль для структура контекста и завершает работу. Функция вызывается один раз для каждого заданного экземпляра подключаемого модуля. Вызов [SccInitialize](../extensibility/sccinitialize-function.md) предшествует этот вызов. Нет проектов по-прежнему могут быть открыты во время вызова `SccUninitialize`.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)