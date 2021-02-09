---
title: Функция СкЦисмултичеккаутенаблед | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 009bc5ba0bb307d0aaee78076266260aa5bb20ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924822"
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
 pContext

окне Структура контекста подключаемого модуля системы управления версиями.

 пбмултичеккаут

заполняет Указывает, включены ли множественные извлечения для этого проекта (ненулевое значение означает, что множественные извлечения поддерживаются).

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Проверка прошла успешно.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Неконкретный сбой.|

## <a name="remarks"></a>Remarks
 Интегрированная среда разработки выполняет две проверки, чтобы определить, могут ли файлы быть извлечены одновременно несколькими пользователями. Во первых, система управления версиями должна поддерживать несколько извлечений. Подключаемый модуль системы управления версиями может указать эту возможность во время инициализации, указав `SCC_CAP_MULTICHECKOUT` . Затем, как вторая проверка, интегрированная среда разработки вызывает эту функцию, чтобы определить, поддерживает ли текущий проект несколько извлечений. Если для выбранного проекта поддерживается несколько извлечений, подключаемый модуль возвращает код успешного выполнения и задает `pbMultiCheckout` для ненулевого ( `TRUE` ) или `FALSE` .

## <a name="see-also"></a>См. также раздел
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
