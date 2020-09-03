---
title: 'IDiaFrameData:: get_type | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 95232ab69d6f30435807764e1177d15d6e4622d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161427"
---
# <a name="idiaframedataget_type"></a>IDiaFrameData::get_type
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает тип кадра, зависящий от компилятора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 заполняет Возвращает значение из перечисления [перечисления стаккфраметипинум](../../debugger/debug-interface-access/stackframetypeenum.md) , которое указывает на тип кадра, зависящий от компилятора.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [Перечисление StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md)
