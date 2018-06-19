---
title: Определение типа (Typedef) JsThreadServiceCallback | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4b7ea4d0d5eaba17269a1777cdf96b5a2a5cda3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568774"
---
# <a name="jsthreadservicecallback-typedef"></a>Определение типа (Typedef) JsThreadServiceCallback
Обратный вызов службы потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 обратный вызов  
 Обратный вызов для фонового рабочего элемента.  
  
 callbackData  
 Аргумент данных для передачи в обратный вызов.  
  
## <a name="remarks"></a>Примечания  
 При вызове JsCreateRuntime узел может указать фоновую службу потока. Если она указана, фоновые рабочие элементы передаются в узел, использующий этот обратный вызов. Предполагается, что узел начнет выполнение фонового рабочего элемента незамедлительно и вернет значение "true" или "false", а среда выполнения будет обрабатывать рабочий элемент в потоке.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)