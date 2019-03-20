---
title: Константы отладчика активных скриптов, перечисления и структуры | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger structures
- Active Script Debugger enumerations
- Active Script Debugger constants
ms.assetid: b80b9207-fb19-4ee2-85fb-41f8c26e7706
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b287001371b80612a2b09a9672e59aff51309cc9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153101"
---
# <a name="active-script-debugger-constants-enumerations-and-structures"></a>Константы, перечисления и структуры отладчика активных скриптов
Следующие константы, перечисления и структуры используются активными интерфейсами отладки.  
  
## <a name="constants-enumerations-and-structures"></a>Константы, перечисления и структуры  
  
|Константы|Описание:|  
|---------------|-----------------|  
|[Константы APPBREAKFLAGS](../../winscript/reference/appbreakflags-enumeration.md)|Показывают текущее состояние отладки для приложений и потоков.|  
|[Константы DEBUG_TEXT](../../winscript/reference/debug-text-constants.md)|Флаги параметров, используемых во время [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).|  
|[Константы TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)|Описывают атрибуты документа.|  
  
|Перечисления|Описание:|  
|------------------|-----------------|  
|[Константы APPBREAKFLAGS](../../winscript/reference/appbreakflags-enumeration.md)|Показывают текущее состояние отладки для приложений и потоков.|  
|[Перечисление APPLICATION_NODE_EVENT_FILTER](../../winscript/reference/application-node-event-filter-enumeration.md)|Показывает узлы, которые должны быть исключены с помощью фильтра.|  
|[Перечисление BREAKPOINT_STATE](../../winscript/reference/breakpoint-state-enumeration.md)|Показывает состояние точки останова.|  
|[Перечисление BREAKREASON](../../winscript/reference/breakreason-enumeration.md)|Показывает, что вызвало прерывание.|  
|[Перечисление BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)|Описывает, как будет происходить продолжение выполнения после точки останова.|  
|[Перечисление DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)|Описывает тип, получаемый для документа.|  
|[Перечисление ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)|Описывает, как будет происходить продолжение выполнения после ошибки времени выполнения.|  
|[Перечисление JS_PROPERTY_ATTRIBUTES](../../winscript/reference/js-property-attributes-enumeration.md)|Задает атрибуты свойства.|  
|[Перечисление JS_PROPERTY_MEMBERS](../../winscript/reference/js-property-members-enumeration.md)|Флаги для задания типа сведений, возвращаемых в запросе к членам объекта.|  
|[Перечисление JsDebugReadMemoryFlags](../../winscript/reference/jsdebugreadmemoryflags-enumeration.md)|Флаги для задания поведения при чтении памяти.|  
|[Перечисление SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md)|Задает набор параметров или возможностей, применяемых к подключенному отладчику.|  
|[Перечисление SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md)|Задает вид создаваемого исключения.|  
|[SOURCE_TEXT_ATTR Constants](../../winscript/reference/source-text-attr-enumeration.md)|Описывают атрибуты отдельного символа исходного текста.|  
  
|Структуры|Описание:|  
|----------------|-----------------|  
|[Структура DebugStackFrameDescriptor](../../winscript/reference/debugstackframedescriptor-structure.md)|Перечисляет кадры стека и объединяет результаты нескольких перечислителей в одном потоке.|  
|[Структура JS_NATIVE_FRAME](../../winscript/reference/js-native-frame-structure.md)|Представляет кадр стека.|  
|[Структура JsDebugPropertyInfo](../../winscript/reference/jsdebugpropertyinfo-structure.md)|Задает сведения о свойстве.|  
|[Структура TEXT_DOCUMENT_ARRAY](../../winscript/reference/text-document-array-structure.md)|Предоставляет набор документов.|