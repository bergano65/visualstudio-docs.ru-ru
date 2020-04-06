---
title: ПОПЛИСФУНК Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c5f8c1683a993915476ff23f1f5d5f2c2aba462
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702060"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Этот обратный вызов поставляется [в SccPopulateList](../extensibility/sccpopulatelist-function.md) IDE и используется плагином управления исходным управлением для обновления `SccPopulateList` списка файлов или каталогов (также поставляемых в функцию).

 Когда пользователь выбирает команду **Get** в IDE, IDE отображает поле списка всех файлов, которые пользователь может получить. К сожалению, IDE не знает точного списка всех файлов, которые пользователь может получить; только плагин имеет этот список. Если другие пользователи добавили файлы в проект управления исходным кодом, эти файлы должны отображаться в списке, но IDE не знает о них. IDE создает список файлов, которые, по его мнению, может получить пользователь. Прежде чем он отображает этот список для пользователя, он называет [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` давая источник управления плагин омрачить возможность добавить и удалить файлы из списка.

## <a name="signature"></a>Сигнатура
 Плагин управления исходным элементом изменяет список, вызывая функцию IDE-реализованной со следующим прототипом:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Параметры
 pvCallerData `pvCallerData` Параметр, передаваемый абонентом (IDE) в [SccPopulateList](../extensibility/sccpopulatelist-function.md). Плагин управления исходным элементом не должен ничего предполагать о содержании этого параметра.

 fAddRemove `TRUE`Если `lpFileName` , это файл, который должен быть добавлен в список файлов. Если `FALSE` `lpFileName` это файл, который должен быть удален из списка файлов.

 nStatus Status `lpFileName` (комбинация `SCC_STATUS` битов; см. [Код статуса файла](../extensibility/file-status-code-enumerator.md) для деталей).

 lpFileName Полный путь каталога имя файла, чтобы добавить или удалить из списка.

## <a name="return-value"></a>Возвращаемое значение

|Значение|Описание|
|-----------|-----------------|
|`TRUE`|Плагин может продолжать вызывать эту функцию.|
|`FALSE`|Там была проблема на стороне IDE (например, вне памяти ситуации). Плагин должен прекратить работу.|

## <a name="remarks"></a>Примечания
 Для каждого файла, который плагин управления исходным источником хочет добавить или удалить `lpFileName`из списка файлов, он называет эту функцию, проходя в . Флаг `fAddRemove` указывает новый файл для добавления в список или старый файл для удаления. Параметр `nStatus` дает статус файла. Когда плагин SCC закончил добавлять и удалять файлы, он возвращается из вызова [SccPopulateList.](../extensibility/sccpopulatelist-function.md)

> [!NOTE]
> Бит `SCC_CAP_POPULATELIST` возможностей необходим для Visual Studio.

## <a name="see-also"></a>См. также
- [Функции обратного вызова, реализованные IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Плагины управления исходным элементом](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Код статуса файла](../extensibility/file-status-code-enumerator.md)
