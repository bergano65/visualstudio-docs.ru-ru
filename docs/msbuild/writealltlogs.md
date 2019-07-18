---
title: WriteAllTLogs | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteAllTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee3f02be5494f85c0fa36be510f0a0c25caf53b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778447"
---
# <a name="writealltlogs"></a>WriteAllTLogs
Записывает журналы отслеживания для всех потоков и контекстов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
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
- [WriteContextTLogs](../msbuild/writecontexttlogs.md)