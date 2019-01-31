---
title: Copy (программный захват) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35558a9ad6a4e7d31103910f3fe71c0a12374c22
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042261"
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