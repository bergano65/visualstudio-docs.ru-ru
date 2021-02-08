---
title: Функция Сккжетверсион | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91daeca1df76f6b624d0eddf9d28222369b2cc4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844545"
---
# <a name="sccgetversion-function"></a>Функция SccGetVersion
Эта функция возвращает номер версии API подключаемого модуля системы управления версиями, поддерживаемый подключаемым модулем системы управления версиями.

## <a name="syntax"></a>Синтаксис

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Параметры
 Нет.

## <a name="return-value"></a>Возвращаемое значение
 `LONG`Тип данных, содержащий номер версии поддерживаемого интерфейса API подключаемого модуля системы управления версиями:

|WORD|Описание|
|----------|-----------------|
|HIWORD|Основной номер версии|
|ловорд|Дополнительный номер версии|

## <a name="remarks"></a>Remarks
 Например, если подключаемый модуль системы управления версиями поддерживает версию 1,3 API подключаемого модуля системы управления версиями, эта функция возвратит 0x0103.

## <a name="see-also"></a>См. также раздел
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
