---
title: DONT_SAVE_VSGLOG_TO_TEMP | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 449c6c1ecdb0644b9b52b6ec12ce867dc34d66c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156104"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет своим наличием, нужно ли сохранять файл журнала графики в каталог временных файлов пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>Значение  
 Символ препроцессора, который имеет наличие или отсутствие определяет, нужно ли сохранять файл журнала графики в каталог временных файлов пользователя. Если этот символ препроцессора определен, имя файла является определенным `VSG_DEFAULT_RUN_FILENAME` относительно текущего каталога захватываемого приложения или представляет собой абсолютный путь; в противном случае это имя, определенное `VSG_DEFAULT_RUN_FILENAME` относительно каталогу временных файлов пользователя, которое не может быть абсолютным путем.  
  
## <a name="remarks"></a>Примечания  
 В зависимости от привилегий пользователя файл журнала графики может быть запрещено сохранять в произвольном месте. Мы рекомендуем сохранять графические журналы в каталог временных файлов пользователя или в другое известное место, если вы не уверены, сможет ли пользователь записать данные в выбранное вами место.  
  
 Чтобы предотвратить сохранение файла журнала графики в каталоге временных файлов, необходимо определить `DONT_SAVE_VSGLOG_TO_TEMP` перед включением `vsgcapture.h`.  
  
## <a name="example"></a>Пример  
 В этом примере показано, как сохранить файл журнала графики в абсолютный путь на главном компьютере.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>См. также:  
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
