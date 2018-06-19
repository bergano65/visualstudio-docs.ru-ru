---
title: Определение типа (Typedef) JsNativeFunction | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 56ef6cdf-4ca9-4f7c-b953-e661addb1a8e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33cf475dd6a17434ea132647b7d8bde833f0de9e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568084"
---
# <a name="jsnativefunction-typedef"></a>Определение типа (Typedef) JsNativeFunction
Обратный вызов функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef _Ret_maybenull_ JsValueRef (CALLBACK * JsNativeFunction)(  
   _In_ JsValueRef callee,  
   _In_ bool isConstructCall,  
   _In_ JsValueRef *arguments,  
   _In_ unsigned short argumentCount  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 вызываемая функция  
 Объект `Function`, который представляет вызванную функцию.  
  
 isConstructCall  
 Указывает, является ли вызов регулярным или "новым".  
  
 аргументы  
 Аргументы для вызова.  
  
 argumentCount  
 Число аргументов.  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Результат вызова (если есть).  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)