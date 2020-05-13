---
title: Функция SccIsMultiCheckout Enabled Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700587"
---
# <a name="sccismulticheckoutenabled-function"></a>Функция SccIsMultiCheckoutEnabled
Эта функция проверяет, позволяет ли плагин управления исходным источником несколько выездов на файл.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Параметры
 pContext

(в) Структура контекста управления исходным элементом.

 pbMultiCheckout

(ваут) Осведяляет, включено ли несколько проверок для этого проекта (ненулевое означает, что поддерживаются несколько выездов).

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Проверка прошла успешно.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Неспецифический сбой.|

## <a name="remarks"></a>Примечания
 IDE проводит две проверки, чтобы определить, могут ли файлы быть проверены одновременно более чем одним пользователем. Во-первых, система управления исходным источником должна поддерживать несколько проверок. Плагин управления исходным элементом может указать эту `SCC_CAP_MULTICHECKOUT`возможность во время инициализации, указав. После этого, как вторая проверка, IDE вызывает эту функцию, чтобы определить, поддерживает ли текущий проект несколько проверок. Если для выбранного проекта поддерживается несколько проверок, плагин возвращает `pbMultiCheckout` код успеха`TRUE`и `FALSE`устанавливается на nonzero ( ) или .

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
