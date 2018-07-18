---
title: Перечисление JsRuntimeAttributes | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsRuntimeAttributes
helpviewer_keywords:
- JsRuntimeAttributes enumeration
ms.assetid: f76d82e9-a695-4d6a-96c1-b3a4d27fed68
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a7917ad5468b8d2924526f953ae444c5d8381eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569064"
---
# <a name="jsruntimeattributes-enumeration"></a>Перечисление JsRuntimeAttributes
Атрибуты среды выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
enum JsRuntimeAttributes;  
```  
  
## <a name="members"></a>Члены  
  
### <a name="values"></a>Значения  
  
|Имя|Описание|  
|----------|-----------------|  
|`JsRuntimeAttributeAllowScriptInterrupt`|Среда выполнения должна поддерживать прерывание надежных сценариев. Это увеличивает количество мест, где среда выполнения будет проверять наличие запроса на прерывание сценария за счет небольшого объема производительности среды выполнения.|  
|`JsRuntimeAttributeDisableBackgroundWork`|Среда выполнения не будет выполнять никаких операций (таких, как сборка мусора) в фоновых потоках.|  
|`JsRuntimeAttributeDisableEval`|С помощью `eval` или `function` конструктор вызовет исключение.|  
|`JsRuntimeAttributeDisableNativeCodeGeneration`|Среда выполнения не будет формировать машинный код.|  
|`JsRuntimeAttributeEnableExperimentalFeatures`|Среда выполнения активирует все экспериментальные функции.|  
|`JsRuntimeAttributeEnableIdleProcessing`|Хост будет вызывать метод `JsIdle`, поэтому необходимо включить обработку бездействия. В противном случае среда выполнения будет управлять памятью немного более агрессивно.|  
|`JsRuntimeAttributeDispatchSetExceptionsToDebugger`|При вызове `JsSetException` также происходит передача исключения отладчику скриптов (если он используется), который получает возможность прервать выполнение.|  
|`JsRuntimeAttributeNone`|Отсутствуют специальные атрибуты.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)