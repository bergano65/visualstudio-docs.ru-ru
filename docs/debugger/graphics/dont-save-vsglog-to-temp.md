---
title: "DONT_SAVE_VSGLOG_TO_TEMP | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 264f67eb9a1fc7f8af739d7eea329de05230c7a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Определяет своим наличием, нужно ли сохранять файл журнала графики в каталог временных файлов пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>Значение  
 Символ препроцессора, который при его наличии или отсутствии определяет, является ли файл журнала графики будет сохранен в папке временных файлов пользователя. Если этот символ определен, то имя файла определяется `VSG_DEFAULT_RUN_FILENAME` является относительным для текущего каталога захватываемого приложения или представляет собой абсолютный путь; в противном случае имя файла определяется `VSG_DEFAULT_RUN_FILENAME` относительно каталога временных файлов пользователя и не может быть Абсолютный путь.  
  
## <a name="remarks"></a>Примечания  
 В зависимости от прав пользователей файл журнала графики не может быть невозможно сохранить в произвольное расположение. Мы рекомендуем, что вы предпочитаете сохранить журналы графики в каталоге временных файлов пользователя, или в другом месте удачной, если вы не уверены, ли бы выбранное местоположение может произвести запись пользователя.  
  
 Чтобы предотвратить файла журнала графики сохраняются в каталоге временных файлов, определенных `DONT_SAVE_VSGLOG_TO_TEMP` перед включением `vsgcapture.h`.  
  
## <a name="example"></a>Пример  
 В этом примере показано, как сохранить файл журнала графики в абсолютный путь на хост-компьютере.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>См. также  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)