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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e91eb566a820f4fe11ceb629643e1815dcb87a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700587"
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
