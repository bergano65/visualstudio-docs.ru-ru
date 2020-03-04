---
title: WriteContextTLogs | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf34ff63b00cf523ba9ef704f4417be4d5cdbf77
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630709"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs

Записывает файлы журнала для текущего контекста.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Параметры

[in] `intermediateDirectory`

 Каталог, в котором хранится журнал отслеживания.

[in] `tlogRootName`

 Имя корневой папки для имени файла журнала.

## <a name="return-value"></a>Возвращаемое значение

 **HRESULT** с установленным битом **SUCCEEDED**, если контекст отслеживания был создан.

## <a name="requirements"></a>Требования

 **Заголовок.** *FileTracker.h*

## <a name="see-also"></a>См. также

- [WriteAllTLogs](../msbuild/writealltlogs.md)