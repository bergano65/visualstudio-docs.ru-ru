---
title: Функция SccBeginBatch (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c7982d8c8c0d71f8c79e9b808be5453d384882d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701200"
---
# <a name="sccbeginbatch-function"></a>Функция SccBeginBatch
Эта функция запускает последовательность операций управления исходным кодом. [SccEndBatch](../extensibility/sccendbatch-function.md) будет вызван, чтобы закончить партию. Эти партии не могут быть вложены.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>Параметры
 Нет.

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Успешно началась серия операций.|
|SCC_E_UNKNOWNERROR|Неспецифический сбой.|

## <a name="remarks"></a>Примечания
 Пакеты управления исходными кодами используются для выполнения одних и тех же операций в нескольких проектах или нескольких контекстах. Пакеты могут использоваться для устранения избыточных диалоговых коробок для одного проекта из пользовательского опыта во время пакетной операции. Функция `SccBeginBatch` и [SccEndBatch](../extensibility/sccendbatch-function.md) используются в качестве пары функций для обозначения начала и конца операции. Они не могут быть вложены. `SccBeginBatch`устанавливает флаг, указывающий на ход пакетной операции.

 В то время как пакетная операция действует, плагин управления исходным кодом должен представлять не более одного диалогового окна для любого вопроса пользователю и применять ответ из этого диалогового окна на всех последующих операциях.

## <a name="see-also"></a>См. также
- [Функции API управления исходным элементом](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
