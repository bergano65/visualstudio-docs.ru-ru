---
title: Функция SccIsMultiCheckoutEnabled | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0b4d13367977081b757fa9b0ef2823154dc348a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679194"
---
# <a name="sccismulticheckoutenabled-function"></a>Функция SccIsMultiCheckoutEnabled
Эта функция проверяет, допускает ли подключаемый модуль системы управления версиями несколько одновременных извлечений с файлом.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Параметры
 pContext

[in] Структура подключаемого модуля контекста исходного элемента управления.

 pbMultiCheckout

[out] Указывает, включены ли несколько одновременных извлечений для этого проекта (ненулевое значение означает, что он поддерживает несколько одновременных извлечений).

## <a name="return-value"></a>Возвращаемое значение
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:

|Значение|Описание:|
|-----------|-----------------|
|SCC_OK|Проверка прошла успешно.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Обнаружена неспецифическая ошибка.|

## <a name="remarks"></a>Примечания
 Интегрированная среда разработки делает две проверки, чтобы определить, если файлы могут извлекаться одновременно более чем одним пользователем. Во-первых системы управления версиями должен поддерживать несколько одновременных извлечений. Подключаемый модуль системы управления версиями можно определить эту возможность во время инициализации, указав `SCC_CAP_MULTICHECKOUT`. После этого в качестве второй проверки интегрированной среды разработки вызывает эту функцию, чтобы определить, поддерживает ли текущий проект несколько одновременных извлечений. Если несколько одновременных извлечений, поддерживается для выбранного проекта, подключаемый модуль возвращает успех кода и задает `pbMultiCheckout` ненулевое значение (`TRUE`) или `FALSE`.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)