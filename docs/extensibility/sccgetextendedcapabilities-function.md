---
title: Функция SccGetExtendedCapabilities | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa6a067a0b9e8358f503228dbc53e20586b84468
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353668"
---
# <a name="sccgetextendedcapabilities-function"></a>Функция SccGetExtendedCapabilities
Эта функция возвращает дополнительные возможности, поддерживаемые подключаемый модуль системы управления версиями.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>Параметры
 pContext

[in] Подключаемый модуль Контекстный указатель исходного элемента управления.

 lSccExCaps

[in] Флаг, указывающий функцию расширенной, для которого нужно проверить (см. в таблице расширенные возможности кода в [флаги возможностей](../extensibility/capability-flags.md) для флаги).

 pbSupported

[out] Возвращает ненулевое значение (`TRUE`) Если указанная возможность поддерживается; в противном случае возвращает 0 (`FALSE`).

## <a name="return-value"></a>Возвращаемое значение
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Операция получения возможностей, успешно завершена.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Произошла ошибка неизвестен или не задан.|

## <a name="remarks"></a>Примечания
 Этот метод вызывается по запросу; то есть, при возможности должна быть проверена, этот метод вызывается для определения, поддерживается возможность. Указывается только один флаг за раз.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)
- [Коды ошибок](../extensibility/error-codes.md)
- [Флаги возможностей](../extensibility/capability-flags.md)