---
title: DONT_SAVE_VSGLOG_TO_TEMP | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e899bc22c64fb3f1ae7fe77f7fa49871ceecf3a2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903238"
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Определяет своим наличием, нужно ли сохранять файл журнала графики в каталог временных файлов пользователя.  

## <a name="syntax"></a>Синтаксис  

```C++  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  

## <a name="value"></a>Значение  
 Символ препроцессора, определяет, является ли файл журнала графики, его наличие или отсутствие сохраняется в каталоге временных файлов пользователя. Если этот символ определен, то имя файла определяется `VSG_DEFAULT_RUN_FILENAME` относительно текущего каталога захватываемого приложения или не является абсолютным; в противном случае имя файла определяется `VSG_DEFAULT_RUN_FILENAME` задается относительно каталога временных файлов пользователя и не может быть Абсолютный путь.  

## <a name="remarks"></a>Примечания  
 В зависимости от привилегий пользователя файл журнала графики может оказаться невозможно сохранить в произвольное расположение. Рекомендуется, вы хотите сохранить журналы графики в каталоге временных файлов пользователя, или в другом расположении работоспособной, если вы не уверены ли расположение, необходимо выбрать могут записываться для пользователя.  

 Чтобы предотвратить файла журнала графики, данные не будут сохранены в каталог временных файлов, определенных `DONT_SAVE_VSGLOG_TO_TEMP` перед включением `vsgcapture.h`.  

## <a name="example"></a>Пример  
 В этом примере показано, как сохранить файл журнала графики в абсолютный путь на хост-компьютере.  

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  

#include <vsgcapture.h>  
```  

## <a name="see-also"></a>См. также  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
