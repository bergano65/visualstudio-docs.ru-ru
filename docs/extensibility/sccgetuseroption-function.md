---
title: Функция SccGetUserOption (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc7b68df3331c1240ad833048940e656da034ccf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700685"
---
# <a name="sccgetuseroption-function"></a>Функция SccGetUserOption
Эта функция извлекает различные пользовательские параметры.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Параметры
 pContext

(в) Указатель контекста управления исходным элементом.

 nOption

(в) Вариант получения (см. Замечания для возможных вариантов).

 lpVal

(ваут) Значение, связанное с опционом.

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Опция была успешно извлечена.|
|SCC_E_OPNOTSUPPORTED|Вариант не поддерживается.|
|SCC_E_NONSPECIFICERROR|Произошла неизвестная ошибка.|

## <a name="remarks"></a>Примечания
 Эта команда поддерживает следующие варианты:

|Пользовательский вариант|Описание|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Определяет, хочет ли пользователь проверить локальную версию файлов. `lpVal`назначается `SCC_USEROPT_COLV_YES` (пользователь хочет проверить локальные `SCC_USEROPT_COLV_NO`файлы) или .|

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Коды ошибок](../extensibility/error-codes.md)
