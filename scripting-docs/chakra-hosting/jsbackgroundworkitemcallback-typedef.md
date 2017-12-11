---
title: "Определение типа (Typedef) JsBackgroundWorkItemCallback | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e6db52e1-830c-46a2-b9f9-cc2d450a1da8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c4281ae1abf1df07d4b6374b6989377c66c1fd7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsbackgroundworkitemcallback-typedef"></a>Определение типа (Typedef) JsBackgroundWorkItemCallback
Обратный вызов фонового рабочего элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef void (CALLBACK *JsBackgroundWorkItemCallback)(  
   _In_opt_ void *callbackData  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 callbackData  
 Аргумент данных, передаваемый в службу потока.  
  
## <a name="remarks"></a>Примечания  
 Аргумент передается в службу потока узла (если есть), что позволяет узлу осуществлять обратный вызов рабочего элемента на фоновом потоке по своему выбору.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)