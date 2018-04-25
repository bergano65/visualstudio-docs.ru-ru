---
title: Copy (программный захват) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67b20a6032a073238f6eb3a8c157c96f95d5c67f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="copy-programmatic-capture"></a>Copy (программный захват)
Копирует содержимое активного файла журнала графики (.vsglog) в новый файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `szNewVSGLog`  
 Имя нового файла журнала графики.  
  
## <a name="remarks"></a>Примечания  
 Для копирования данных графики в новый файл должны быть уже захвачены какие-либо данные графики; в противном случае ничего не произойдет.