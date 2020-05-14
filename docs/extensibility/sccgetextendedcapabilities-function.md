---
title: Функция SccGetExtendedCapabilities (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5247f2de7ffc63db7235f915c72b3274b8fee5f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700721"
---
# <a name="sccgetextendedcapabilities-function"></a>Функция SccgetExtendedCapabilities
Эта функция возвращает дополнительные возможности, поддерживаемые плагином управления исходным управлением.

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

(в) Указатель контекста управления исходным элементом.

 lSccExCaps

(в) Флаг, определяющий расширенную возможность для тестирования (см. таблицу расширенного кода возможностей в [флагах возможностей](../extensibility/capability-flags.md) для возможных флагов).

 pbПоддерживается

(ваут) Возвращает ненулевой`TRUE`( ), если указанная возможность поддерживается; в противном`FALSE`случае, возвращаетнулно ноль ().

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Операция по обеспечению возможностей успешно завершена.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Произошла неизвестная или неопределенная ошибка.|

## <a name="remarks"></a>Примечания
 Этот метод называется по требованию; то есть, когда возможность должна быть проверена, этот метод называется, чтобы определить, поддерживается ли эта возможность. Указан только один флаг за один раз.

## <a name="see-also"></a>См. также
- [Функции API управления исходным элементом](../extensibility/source-control-plug-in-api-functions.md)
- [Коды ошибок](../extensibility/error-codes.md)
- [Флаги возможностей](../extensibility/capability-flags.md)
