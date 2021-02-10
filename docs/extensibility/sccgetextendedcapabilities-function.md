---
title: Функция Сккжетекстендедкапабилитиес | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1256c9110fe538b4a5d52b165c71216b6537f2c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958418"
---
# <a name="sccgetextendedcapabilities-function"></a>Функция Сккжетекстендедкапабилитиес
Эта функция возвращает дополнительные возможности, поддерживаемые подключаемым модулем системы управления версиями.

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

окне Указатель контекста для подключаемого модуля системы управления версиями.

 лскцекскапс

окне Флаг, указывающий расширенную возможность для тестирования (дополнительные флаги см. в таблице кода расширенной возможности в [флагах возможностей](../extensibility/capability-flags.md) ).

 пбсуппортед

заполняет Возвращает ненулевое значение ( `TRUE` ), если указанная возможность поддерживается; в противном случае возвращает ноль ( `FALSE` ).

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Операция получения возможности успешно завершена.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Произошла неизвестная или Неуказанная ошибка.|

## <a name="remarks"></a>Remarks
 Этот метод вызывается по запросу; то есть, когда необходимо проверить возможность, этот метод вызывается для определения того, поддерживается ли эта возможность. Указан только один флаг за раз.

## <a name="see-also"></a>См. также раздел
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Коды ошибок](../extensibility/error-codes.md)
- [Флаги возможностей](../extensibility/capability-flags.md)
