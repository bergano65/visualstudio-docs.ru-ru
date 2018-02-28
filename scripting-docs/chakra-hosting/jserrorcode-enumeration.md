---
title: "Перечисление JsErrorCode | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsErrorCode
helpviewer_keywords:
- JsErrorCode enumeration
ms.assetid: 4902f3f3-47a5-4e74-9c29-f96eeecbcda9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b09babd38505c5619f414d2e349cd52b3596ceac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jserrorcode-enumeration"></a>Перечисление JsErrorCode
Код ошибки, возвращаемый API размещения Chakra.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
enum JsErrorCode : unsigned int;  
```  
  
## <a name="members"></a>Члены  
  
### <a name="values"></a>Значения  
  
|Имя|Описание|  
|----------|-----------------|  
|`JsErrorAlreadyDebuggingContext`|Контекст невозможно перевести в состояние отладки, потому что он уже находится в состоянии отладки.|  
|`JsErrorAlreadyProfilingContext`|Контекст не может запустить профилирование, потому что профилирование уже выполняется.|  
|`JsErrorArgumentNotObject`|API размещения, который работает со значениями объекта, был вызван со значением без объектов.|  
|`JsErrorBadSerializedScript`|Использовался неверный сериализованный скрипт, или сериализованный скрипт был сериализован с помощью другой версии ядра Chakra.|  
|`JsErrorCannotDisableExecution`|Среда выполнения не поддерживает прерывания надежного сценария.|  
|`JsErrorCannotSerializeDebugScript`|Сценарии не могут быть сериализованы в контекстах отладки.|  
|`JsErrorCategoryEngine`|Категория ошибок, к которой относятся ошибки, имеющие место в самом ядре.|  
|`JsErrorCategoryFatal`|Категория ошибок, которые являются неустранимыми и означают сбой подсистемы.|  
|`JsErrorCategoryScript`|Категория ошибок, связанная с ошибками в скрипте.|  
|`JsErrorCategoryUsage`|Категория ошибок, связанная с неверным использованием самого API.|  
|`JsErrorFatal`|Произошла неустранимая ошибка в подсистеме.|  
|`JsErrorHeapEnumInProgress`|Перечисление кучи в настоящее время выполняется в контексте скрипта.|  
|`JsErrorIdleNotEnabled`|Уведомление о бездействии, выдаваемое, если на узле не включена обработка бездействия.|  
|`JsErrorInDisabledState`|Среда выполнения находится в отключенном состоянии.|  
|`JsErrorInExceptionState`|Обработчик находится в состоянии исключения, и вызвать API невозможно до устранения исключения.|  
|`JsErrorInObjectBeforeCollectCallback`|Операция не поддерживается в объекте до обратного вызова сбора.<br /><br /> Это значение перечисления поддерживается только в режиме Edge.|  
|`JsErrorInProfileCallback`|Контекст скрипта находится в процессе обратного вызова профиля.|  
|`JsErrorInThreadServiceCallback`|Обратный вызов службы потока выполняется в данный момент.|  
|`JsErrorInvalidArgument`|Недопустимый аргумент для API размещения.|  
|`JsErrorNoCurrentContext`|API размещения требует, чтобы контекст был актуальным, однако актуальный контекст отсутствует.|  
|`JsErrorNotImplemented`|API размещения еще не реализован.|  
|`JsErrorNullArgument`|Аргумент для API размещения имел значение null в контексте, где значение null не допускается.|  
|`JsErrorObjectNotInspectable`|Невозможно выполнить распаковывание объекта в указатель `IInspectable` .<br /><br /> Это значение перечисления поддерживается только в режиме Edge.|  
|`JsErrorOutOfMemory`|В подсистеме Chakra закончилась свободная память.|  
|`JsErrorPropertyNotSymbol`|API размещения, который работает с идентификаторами свойств символов, однако был вызван с идентификатором свойства объекта, не являющегося символом. Код ошибки возвращается идентификатором `JsGetSymbolFromPropertyId` , если функция вызывается с идентификатором свойства объекта, не являющегося символом.<br /><br /> Это значение перечисления поддерживается только в режиме Edge.|  
|`JsErrorPropertyNotString`|API размещения, который работает с идентификаторами свойств строк, однако был вызван с идентификатором свойства объекта, не являющегося строкой. Код ошибки возвращается существующим идентификатором `JsGetPropertyNamefromId` , если функция вызывается с идентификатором свойства объекта, не являющегося строкой.<br /><br /> Это значение перечисления поддерживается только в режиме Edge.|  
|`JsErrorRuntimeInUse`|Невозможно удалить среду выполнения, которая до сих пор используется.|  
|`JsErrorScriptCompile`|Не удалось скомпилировать JavaScript.|  
|`JsErrorScriptEvalDisabled`|Скрипт был завершен, потому что попытался использовать `eval` или `function` , а метод Eval был отключен.|  
|`JsErrorScriptException`|Возникло исключение JavaScript при выполнении скрипта.|  
|`JsErrorScriptTerminated`|Сценарий был завершен из-за запроса на приостановку среды выполнения.|  
|`JsErrorWrongRuntime`|API размещения был вызван с объектом, созданным в другой среде выполнения JavaScript.|  
|`JsErrorWrongThread`|API размещения был вызван для неправильного потока.|  
|`JsNoError`|Код ошибки метода Success.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)