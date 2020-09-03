---
title: 'IDiaEnumSourceFiles:: Next | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Next method
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fe965043ad854c31c933447452f1039ba40cd04a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189822"
---
# <a name="idiaenumsourcefilesnext"></a>IDiaEnumSourceFiles::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает указанное число исходных файлов в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Next (   
   ULONG            celt,  
   IDiaSourceFile** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 окне Число извлекаемых исходных файлов в перечислителе.  
  
 rgelt  
 заполняет Массив, который должен быть заполнен объектами [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , представляющими нужные исходные файлы.  
  
 pceltFetched  
 заполняет Возвращает количество исходных файлов в выбранном перечислителе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если нет других исходных файлов. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession:: Финдлинесбилиненум](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
