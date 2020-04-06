---
title: Функция SccGetVersion (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a563a7d1d65dc4c6564abd4e337242eea1aa9924
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700677"
---
# <a name="sccgetversion-function"></a>Функция SccGetVersion
Эта функция получает номер версии подключаемого к источнику API управления, поддерживаемый плагином управления исходным элементом.

## <a name="syntax"></a>Синтаксис

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Параметры
 Нет.

## <a name="return-value"></a>Возвращаемое значение
 Тип `LONG` данных, содержащий номер версии поддерживаемого API подключаемого элемента управления исходным управлением:

|WORD|Описание|
|----------|-----------------|
|ПРИВЕТСЛОВОЕ СЛОВО|Основной номер версии|
|СЛОВО|Дополнительный номер версии|

## <a name="remarks"></a>Примечания
 Например, если плагин управления исходным источником поддерживает версию 1.3 API подключаемого к исходного управления, эта функция будет возвращать 0x0103.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
