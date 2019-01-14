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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ca5bfbdae319aff8d90686deb32a5c7348fa74e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985541"
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
 **Заголовок:** *FileTracker.h*  
  
## <a name="see-also"></a>См. также  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)