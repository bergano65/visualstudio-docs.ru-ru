---
title: IDiaFrameData::get_type | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0209a715ece3e1fa760080ad7ccf0803d11950df
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834595"
---
# <a name="idiaframedatagettype"></a>IDiaFrameData::get_type
Извлекает тип пакета специфичные для компилятора.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает значение из [перечисление StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md) перечисление, указывающее тип кадра специфичные для компилятора.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [Перечисление StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md)