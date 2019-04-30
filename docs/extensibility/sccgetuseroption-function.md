---
title: Функция SccGetUserOption | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b237ded8ac0d22500986a9d390834147f24a2c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433192"
---
# <a name="sccgetuseroption-function"></a>Функция SccGetUserOption
Эта функция получает различные параметры конкретного пользователя.

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

[in] Подключаемый модуль Контекстный указатель исходного элемента управления.

 nOption

[in] Параметр, чтобы получить (см. в разделе "Примечания" для возможные варианты).

 lpVal

[out] Значение, связанное с параметром.

## <a name="return-value"></a>Возвращаемое значение
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Параметр был успешно извлечен.|
|SCC_E_OPNOTSUPPORTED|Параметр не поддерживается.|
|SCC_E_NONSPECIFICERROR|Произошла неизвестная ошибка.|

## <a name="remarks"></a>Примечания
 Эта команда поддерживает следующие параметры:

|Параметр User|Описание|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Определяет, хочет ли пользователь извлечь локальную версию файлов. `lpVal` назначается `SCC_USEROPT_COLV_YES` (пользователю нужно извлечь локальных файлов) или `SCC_USEROPT_COLV_NO`.|

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Коды ошибок](../extensibility/error-codes.md)