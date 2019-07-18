---
title: Функция SccCloseProject | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5a5fe721a3b51f4d3f210e7f2d5450e4f4bc6f41
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333934"
---
# <a name="scccloseproject-function"></a>Функция SccCloseProject
Эта функция закрывает проект, отмечающую конец конкретного сеанса.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Параметры
 pvContext структура подключаемого модуля контекста исходного элемента управления.

## <a name="return-value"></a>Возвращаемое значение
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Проект был успешно закрыт.|
|SCC_E_PROJNOTOPEN|Проект не открыт.|
|SCC_E_NOTAUTHORIZED|Пользователю запрещено для этой операции.|
|SCC_E_NONSPECIFICERROR|Обнаружена неспецифическая ошибка.|

## <a name="remarks"></a>Примечания
 [SccOpenProject](../extensibility/sccopenproject-function.md) всегда вызывается перед этой функцией. Вызов этой функции выполняется путем вызова либо `SccOpenProject` функции или [SccUninitialize](../extensibility/sccuninitialize-function.md), для завершения подключения к системе управления версиями, полностью.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)