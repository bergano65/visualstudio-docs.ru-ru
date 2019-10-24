---
title: Функция Сккжетверсион | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69078200743f30c4ecfedce8e9be05ef9e7ce20b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721481"
---
# <a name="sccgetversion-function"></a>Функция SccGetVersion
Эта функция возвращает номер версии API подключаемого модуля системы управления версиями, поддерживаемый подключаемым модулем системы управления версиями.

## <a name="syntax"></a>Синтаксис

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Параметры
 Отсутствует.

## <a name="return-value"></a>Возвращаемое значение
 @No__t_0 тип данных, содержащий номер версии поддерживаемого интерфейса API подключаемого модуля системы управления версиями:

|WORD|Описание|
|----------|-----------------|
|HIWORD|Основной номер версии|
|ловорд|Дополнительный номер версии|

## <a name="remarks"></a>Заметки
 Например, если подключаемый модуль системы управления версиями поддерживает версию 1,3 API подключаемого модуля системы управления версиями, эта функция возвратит 0x0103.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)