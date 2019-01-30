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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 026fb2dedbfb67aa64c1a8e074e8c4017f9e69aa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955808"
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
 [WriteAllTLogs](../msbuild/writealltlogs.md)