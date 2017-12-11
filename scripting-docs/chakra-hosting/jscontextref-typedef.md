---
title: "Определение типа (Typedef) JsContextRef | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8586bfcc-bb24-430d-a6f2-1a3b3e34ec2e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec1300717b59c3b901665b39ca0102988e83e853
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jscontextref-typedef"></a>Определение типа (Typedef) JsContextRef
Ссылка на контекст скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef JsRef JsContextRef;  
```  
  
## <a name="remarks"></a>Примечания  
 Каждый контекст скрипта содержит собственный глобальный объект, отличающийся от глобальных объектов других контекстов скрипта.  
  
 Многие API размещения Chakra требуют «активного» скриптового контекста, настроить который можно с помощью `JsSetCurrentContext`. узлы-API Chakra, для которых необходимо задать контекст, будут обозначены в своей документации.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)