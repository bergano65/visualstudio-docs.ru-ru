---
title: VSG_DEFAULT_RUN_FILENAME | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb0853e51a5c56ed36babb3474d33adac480e8e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
Определяет имя файла журнала графики по умолчанию.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Параметры  
 `filename`  
 Имя файла журнала графики, присваиваемое по умолчанию файлу журнала графики при захвате данных графики программными средствами.  
  
## <a name="value"></a>Значение  
 Строковый литерал, который представляет имя файла журнала графики. По умолчанию это "default.vsglog".  
  
```C++  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Примечания  
 Если определен символ препроцессора `DONT_SAVE_VSGLOG_TO_TEMP`, имя файла является относительным для текущего каталога захватываемого приложения или представляет собой абсолютный путь; в противном случае это имя относительно каталога временных файлов пользователя, которое не может быть абсолютным путем.  
  
 Чтобы изменить определенное имя файла, необходимо переопределить его до включения `vsgcapture.h` в программе.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как изменить имя файла захвата по умолчанию:  
  
```C++  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>См. также  
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)