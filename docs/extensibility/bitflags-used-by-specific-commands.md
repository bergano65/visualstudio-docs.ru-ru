---
title: Bitflags, используемые конкретными командами (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa1fd8bf025d665977e87dc8b88da724ade5a8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740014"
---
# <a name="bitflags-used-by-specific-commands"></a>Битфлаги, используемые определенными командами
Поведение ряда функций в API подключаемых источников может быть изменено, установив один или несколько битов в одно значение. Эти значения известны как bitflags. Различные bitflags, используемые API подключаемых источников управления, подробно описаны здесь, сгруппированы по функции, которая их использует.

## <a name="checked-out-flag"></a>Проверенный флаг
 Этот флаг может быть установлен для [SccAdd](../extensibility/sccadd-function.md) или [SccCheckin](../extensibility/scccheckin-function.md).

|Флаг|Значение|Описание|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Храните файл проверили.|

## <a name="add-flags"></a>Добавление флагов
 Эти флаги используются [SccAdd](../extensibility/sccadd-function.md).

|Флаг|Значение|Описание|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Ожидается, что плагин управления исходным элементом автоматически определяет, является ли файл текстовым или двоичным.|
|`SCC_FILETYPE_TEXT`|0x01|Тип файла — это текст.|
|`SCC_FILETYPE_BINARY`|0x04|Тип файла является двоичным. **Примечание:** `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` и флаги являются взаимоисключающими.   Установите точно один или ни один.|
|`SCC_ADD_STORELATEST`|0x02|Храните только последнюю версию (без дельт).|

## <a name="diff-flags"></a>Дифф флаги
 [SccDiff](../extensibility/sccdiff-function.md) использует эти флаги для определения сферы действия дифф. Флаги `SCC_DIFF_QD_xxx` являются взаимоисключающими. Если какой-либо из них указан, то визуальной обратной связи не должно быть дано. В «быстром диффе» (КД) плагин не определяет, чем отличается файл, только если он отличается. Если ни один из этих флагов не указан, делается "визуальный дифф"; вычисляются и отображаются подробные различия файлов. Если запрошенный qD не поддерживается, плагин переходит к следующему лучшему. Например, если IDE запрашивает чек, а плагин не поддерживает ее, плагин делает полностью проверяемую проверку (по-прежнему гораздо быстрее, чем визуальный дисплей).

|Флаг|Значение|Описание|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Игнорировать различия в делах.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Игнорировать различия в белом пространстве. **Примечание:**  И `SCC_DIFF_IGNORECASE` `SCC_DIFF_IGNORESPACE` флаги являются необязательным bitflags.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|Сравнив весь содержимое файла.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|«D по чексуму.|
|`SCC_DIFF_QD_TIME`|0x0040|«D по дате файла/штампу времени.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Это маска, используемая для проверки всех бийфлагов. Она не должна передаваться в функцию; три битфлага «D» являются взаимоисключающими. «D всегда означает отсутствие отображения uI.|

## <a name="populatelist-flag"></a>Флаг PopulateList
 Этот флаг используется [SccPopulateList](../extensibility/sccpopulatelist-function.md) в `fOptions` параметре.

|Флаг|Значение|Описание|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|IDE передает каталоги, а не файлы.|

## <a name="populatedirlist-flags"></a>Флаги PopulateDirList
 Эти флаги используются [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) в параметре. `fOptions`

|Значение параметра|Значение|Описание|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Изучите только один уровень каталогов для каталогов (это по умолчанию).|
|SCC_PDL_RECURSIVE|0x0001|Рекурсивно изучить все каталоги в каждом данном каталоге.|
|SCC_PDL_INCLUDEFILES|0x0002|Включите имена файлов в процесс экспертизы.|

## <a name="openproject-flags"></a>Флаги OpenProject
 Эти флаги используются [SccOpenProject](../extensibility/sccopenproject-function.md) в параметре. `dwFlags`

|Значение параметра|Значение|Описание|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Если проект не существует в элементе управления исходным источником, создайте его. Если этот флаг не установлен, подсможете `SCC_OP_SILENTOPEN` пользователю создать проект (если флаг не указан).|
|SCC_OP_SILENTOPEN|0x00000002L|Не побуждаете пользователя создать проект; просто `SCC_E_UNKNOWNPROJECT`вернуться .|

## <a name="get-flags"></a>Получить флаги
 Эти флаги используются [SccGet](../extensibility/sccget-function.md) и [SccCheckout.](../extensibility/scccheckout-function.md)

|Флаг|Значение|Описание|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|IDE передает каталоги, а не файлы: Получите все файлы в этих каталогах.|
|`SCC_GET_RECURSIVE`|0x00000002L|IDE проходит каталоги: Получить эти каталоги и все их субдиректоров.|

## <a name="noption-values"></a>значения nOption
 Эти флаги используются [SccSetOption](../extensibility/sccsetoption-function.md) в параметре. `nOption`

|Флаг|Значение|Описание|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Установите состояние очереди событий.|
|`SCC_OPT_USERDATA`|0x00000002L|Укажите данные пользователя для `SCC_OPT_NAMECHANGEPFN`.|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE может обрабатывать отмену.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Установите обратный вызов для изменения имени.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Отключение элемента управления источниками подключаемых систем проверки uI и не устанавливает рабочий каталог.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Добавьте из системы управления исходным элементом указать рабочий каталог. Попробуйте поделиться в ассоциированном проекте, если он является прямым потомком.|

## <a name="dwval-bitflags"></a>dwVal битфлаги
 Эти флаги используются [SccSetOption](../extensibility/sccsetoption-function.md) в параметре. `dwVal`

|Флаг|Значение|Описание|Используется `nOption` по стоимости|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Приостанавливает действие очереди событий.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Позволяет выходить в очередь событий.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(По умолчанию) Не имеет режима отмены; плагин должен поставлять при желании.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|Ручки IDE отменяем.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(По умолчанию) OK, чтобы проверить из плагина uI; рабочий каталог установлен.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Нет плагина uI проверки, нет рабочего каталога.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>См. также
- [Плагины управления исходным элементом](../extensibility/source-control-plug-ins.md)
