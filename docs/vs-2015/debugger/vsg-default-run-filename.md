---
title: VSG_DEFAULT_RUN_FILENAME | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07407dc0a50da935d8d5a9fa0eed213633adbe4f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801060"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет имя файла журнала графики по умолчанию.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Параметры  
 `filename`  
 Имя файла журнала графики, присваиваемое по умолчанию файлу журнала графики при захвате данных графики программными средствами.  
  
## <a name="value"></a>Значение  
 Строковый литерал, который представляет имя файла журнала графики. По умолчанию это "default.vsglog".  
  
```cpp  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Примечания  
 Если определен символ препроцессора `DONT_SAVE_VSGLOG_TO_TEMP`, имя файла является относительным для текущего каталога захватываемого приложения или представляет собой абсолютный путь; в противном случае это имя относительно каталога временных файлов пользователя, которое не может быть абсолютным путем.  
  
 Чтобы изменить определенное имя файла, необходимо переопределить его до включения `vsgcapture.h` в программе.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как изменить имя файла захвата по умолчанию:  
  
```cpp  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>См. также  
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)



