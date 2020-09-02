---
title: 'Идиаинжектедсаурце:: get_sourceCompression | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e8cafcaf3d245ac2310b93c16812327c381854d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192427"
---
# <a name="idiainjectedsourceget_sourcecompression"></a>IDiaInjectedSource::get_sourceCompression
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает индикатор используемого сжатия источника.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_sourceCompression (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 заполняет Возвращает индикатор используемого сжатия источника. Нулевое значение указывает, что сжатие источника не использовалось.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Значение, возвращаемое этим методом, зависит от используемого компилятора. Например, компилятор может использовать кодирование длины выполнения или сжатие в стиле Хаффмана.  
  
## <a name="see-also"></a>См. также:  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
