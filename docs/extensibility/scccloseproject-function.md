---
title: Функция SccCloseProject (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71df385bc0cf42c2437abfd117c2f84bda5b5432
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701048"
---
# <a name="scccloseproject-function"></a>Функция SccCloseProject
Эта функция закрывает проект, отмечая окончание определенной сессии.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Параметры
 pvContext Структура контекста управления исходным элементом.

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Проект был успешно закрыт.|
|SCC_E_PROJNOTOPEN|В настоящее время проект не открыт.|
|SCC_E_NOTAUTHORIZED|Пользователю не разрешается выполнять эту операцию.|
|SCC_E_NONSPECIFICERROR|Неспецифический сбой.|

## <a name="remarks"></a>Примечания
 [SccOpenProject](../extensibility/sccopenproject-function.md) всегда называется до этой функции. Затем за вызовом к этой функции `SccOpenProject` следует вызов либо к функции, либо к [SccUninitialize,](../extensibility/sccuninitialize-function.md)который полностью завершает подключение к системе управления исходным ресурсом.

## <a name="see-also"></a>См. также
- [Функции API управления исходным элементом](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
