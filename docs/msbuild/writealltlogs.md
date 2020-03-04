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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7eadb30ee25b1182be5deb12feebd5ef280ebf4b
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630682"
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