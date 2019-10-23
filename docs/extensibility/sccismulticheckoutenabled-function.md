---
title: Функция СкЦисмултичеккаутенаблед | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd8fb5439ac68200ba1a3bbf3af665595528173e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721073"
---
# <a name="sccismulticheckoutenabled-function"></a>Функция SccIsMultiCheckoutEnabled
Эта функция проверяет, допускает ли подключаемый модуль системы управления версиями многократное извлечение файла.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Параметры
 пконтекст

окне Структура контекста подключаемого модуля системы управления версиями.

 пбмултичеккаут

заполняет Указывает, включены ли множественные извлечения для этого проекта (ненулевое значение означает, что множественные извлечения поддерживаются).

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|значения|Описание|
|-----------|-----------------|
|SCC_OK|Проверка прошла успешно.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Неконкретный сбой.|

## <a name="remarks"></a>Заметки
 Интегрированная среда разработки выполняет две проверки, чтобы определить, могут ли файлы быть извлечены одновременно несколькими пользователями. Во первых, система управления версиями должна поддерживать несколько извлечений. Подключаемый модуль системы управления версиями может указать эту возможность во время инициализации, указав `SCC_CAP_MULTICHECKOUT`. Затем, как вторая проверка, интегрированная среда разработки вызывает эту функцию, чтобы определить, поддерживает ли текущий проект несколько извлечений. Если для выбранного проекта поддерживается несколько извлечений, подключаемый модуль возвращает код успешного выполнения и задает `pbMultiCheckout` ненулевому (`TRUE`) или `FALSE`.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)