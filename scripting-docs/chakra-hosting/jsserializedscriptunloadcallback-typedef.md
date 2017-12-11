---
title: "Определение типа (Typedef) JsSerializedScriptUnloadCallback | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f485d31367f189231d354c653c8e58cc8656eb9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializedscriptunloadcallback-typedef"></a>Определение типа JsSerializedScriptUnloadCallback
Вызывается средой выполнения по завершении обработки всех ресурсов, связанных с выполнением скрипта.     Вызывающий объект на этом этапе должен освободить источник, если он загружен, байтовый код и контекст.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `sourceContext`  
 Контекст, передаваемый в `JsParseSerializedScriptWithCallback` или `JsRunSerializedScriptWithCallback`.  
  
## <a name="remarks"></a>Примечания  
  
> [!WARNING]
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)