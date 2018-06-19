---
title: Определение типа (Typedef) JsRuntimeHandle | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d3c0344e203c58691048c55ba4080c6c86c1c643
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568714"
---
# <a name="jsruntimehandle-typedef"></a>Определение типа (Typedef) JsRuntimeHandle
Обработчик среды выполнения Chakra.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## <a name="remarks"></a>Примечания  
 Каждая среда выполнения Chakra имеет свой независимый механизм выполнения, JIT-компилятор и кучу сборщика мусора. Таким образом, каждая среда выполнения полностью изолирована от других сред.  
  
 Среды выполнения можно использовать в любом потоке, но только один поток может осуществить вызов в среду выполнения в любое время.  
  
> [!WARNING]
>  В отличие от других ссылок на объекты в хосте-API Chakra, JsRuntimeHandle — это не собранный мусор, поскольку содержит мусор, собранный самой кучей. Среда выполнения будет существовать, пока JsDisposeRuntime вызывается.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)