---
title: Функция SccEndBatch (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51fe7e0bc0d417ffa182fbc68fd2779ed0b625d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700926"
---
# <a name="sccendbatch-function"></a>Функция SccEndBatch
Эта функция завершает серию операций управления исходным кодом. Эти партии не могут быть вложены.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Параметры
 Нет.

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Пакет операций успешно завершен.|
|SCC_E_UNKNOWNERROR|Неспецифический сбой.|

## <a name="remarks"></a>Примечания
 Пакеты управления исходными кодами используются для выполнения одних и тех же операций управления исходными кодами в нескольких проектах или нескольких контекстах. Пакеты могут использоваться для устранения избыточных диалогов ы от пользовательского опыта во время пакетной операции. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) и `SccEndBatch` функция используются в качестве пары для обозначения начала и конца операции. Они не могут быть вложены.

## <a name="see-also"></a>См. также
- [Функции API управления исходным элементом](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
