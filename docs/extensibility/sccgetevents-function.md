---
title: Функция SccGetEvents Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91b3debf0e686ceece3048cf3d92b629e3359edd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700821"
---
# <a name="sccgetevents-function"></a>Функция SccGetEvents
Эта функция извлекает событие состояния в очереди.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccGetEvents (
   LPVOID pvContext,
   LPSTR  lpFileName,
   LPLONG lpStatus,
   LPLONG pnEventsRemaining
);
```

### <a name="parameters"></a>Параметры
 pvКонтекст

(в) Структура контекста управления исходным элементом.

 lpFileName

(в, вне) Буфер, где плагин управления исходным элементом помещает возвращенное имя файла (до _MAX_PATH символов).

 lpStatus

(в, вне) Возвращает код состояния (см. [код статуса файла](../extensibility/file-status-code-enumerator.md) для возможных значений).

 pnEventsRemaining

(в, вне) Возвращает количество записей, оставшихся в очереди после этого вызова. Если этот номер большой, абонент может позвонить в [Scc's'ryInfo,](../extensibility/sccqueryinfo-function.md) чтобы получить всю информацию сразу.

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Получить события удалось.|
|SCC_E_OPNOTSUPPORTED|Эта функция не поддерживается.|
|SCC_E_NONSPECIFICERROR|Неспецифический сбой.|

## <a name="remarks"></a>Примечания
 Эта функция вызывается во время обработки простоя, чтобы увидеть, были ли какие-либо обновления статуса для файлов под контролем источника. Плагин управления исходным элементом поддерживает состояние всех файлов, о них он знает, и всякий раз, когда изменение статуса отмечается плагином, статус и связанный файл сохраняются в очереди. При `SccGetEvents` вызове верхний элемент очереди извлекается и возвращается. Эта функция ограничена для возврата только ранее кэшированной информации и должна иметь очень быстрый оборот (т.е. отсутствие чтения диска или запрос ат-системы управления исходным источником для статуса); в противном случае производительность IDE может начать ухудшаться.

 Если нет обновления статуса для отчета, элемент управления исходным элементом хранит `lpFileName`пустую строку в буфере, на которую указывается. В противном случае плагин сохраняет полное имя файла, для которого была изменена информация о статусе, и возвращает соответствующий код статуса (одно из значений, подробно описанных в [коде статуса файла).](../extensibility/file-status-code-enumerator.md)

## <a name="see-also"></a>См. также
- [Функции API управления исходным элементом](../extensibility/source-control-plug-in-api-functions.md)
- [Код статуса файла](../extensibility/file-status-code-enumerator.md)
