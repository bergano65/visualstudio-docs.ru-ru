---
title: Функция SccUninitialize (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4706ddf28949af4fe1bba01c32b2c64c9156d51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700232"
---
# <a name="sccuninitialize-function"></a>Функция SccUninitialize
Эта функция очищает все выделения или открытые соединения, созданные предыдущим вызовом [в SccInitialize](../extensibility/sccinitialize-function.md) в рамках подготовки к закрытию плагина управления исходным кодом.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Параметры
 pvКонтекст

(в) Указатель на структуру контекста управления исходным элементом, созданную в [SccInitialize.](../extensibility/sccinitialize-function.md)

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Очистка завершена успешно.|

## <a name="remarks"></a>Примечания
 Плагин управления исходным элементом отвечает за подготовку к закрытию и за освобождение памяти, выделенной плагином для структуры контекста. Функция вызывается один раз для каждого данного экземпляра плагина. Вызов в [SccInitialize](../extensibility/sccinitialize-function.md) предшествует этому вызову. Никакие проекты по-прежнему не могут `SccUninitialize`быть открыты во время звонка.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
