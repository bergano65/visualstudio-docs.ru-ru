---
title: "Структур и объединений | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "структуры [пакет SDK Visual Studio]"
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Структур и объединений
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Следующие структуры и объединения в пакете SDK для отладки Visual Studio.  
  
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 Задает идентификатор процесса, которая может быть либо системный идентификатор GUID.  
  
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 Описывает условия, при которых точка останова сгорит.  
  
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 Описывает разрешение точки останова ошибки, включая расположение программы, а поток.  
  
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 Указывает тип структуры, используемый для описания расположения точки останова.  
  
 [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 Задает компоненты, которые описывают расположение точки останова по адресу в коде.  
  
 [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 Описывает местоположение точки останова, которая непосредственно в привязана к адресу отлаживаемой программы.  
  
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 Описывает местоположение точки останова на линии в исходном файле кода.  
  
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 Описывает расположение смещения точки останова в функции в коде.  
  
 [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 Используется для установки точки останова кода основано на строку, которую пользователь может ввести из интегрированной среды разработки.  
  
 [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 Используется для установки точки останова для данных, которые основаны на строку, которую пользователь может ввести из интегрированной среды разработки.  
  
 [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 Описывает разрешение точки останова на определенном местоположении.  
  
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 Описывает количество и условия, на котором точка останова будет предоставляется после ранее для передачи.  
  
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 Содержит сведения, необходимые для реализации точку останова.  
  
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 Содержит сведения, необходимые для реализации точку останова \(аналогично [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) структура но включает идентификатор GUID поставщика, ограничение и данные точки трассировки\).  
  
 [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 Описывает местоположение точки останова кода.  
  
 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 Описывает результат привязки точку останова в данных.  
  
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 Описывает связанные данные точки останова для точки останова кода или точки останова для данных.  
  
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 Определяет структуру разрешения расположения точки останова.  
  
 [BSTR\_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 Описывает массив строк.  
  
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 Указывает сведения о типе поля принятом из метаданных.  
  
 [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md)  
 Описывает вызов функции или метода.  
  
 [COMPUTER\_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 Описывает компьютер, на котором отладчик работает.  
  
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 Описывает список GUID.  
  
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)  
 Описывает контекст памяти или контекст кода.  
  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 Описывает адрес в отлаживаемом программе.  
  
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 Представляет один из нескольких разных типов адресов.  
  
 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 Определяет пользовательские средства просмотра или визуализатора типа.  
  
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 Описывает свойство отладки, которое, в свою очередь, описывает объект иерархической характера, которая имеет имя, тип и значение.  
  
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 Описывает ссылку.  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 Описывает разборку в интегрированной среде разработки для отображения.  
  
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 Описывает исключение или ошибка во время выполнения, создаваемые отлаживаемой программой.  
  
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)  
 Описывает локальную переменную, параметр или другое поле.  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 Описывает кадр стека.  
  
 [GUID\_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 Описывает массив уникальных идентификаторов доступных обработчиков отладки.  
  
 [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 Используется для задания сведений о JustMyCode для модуля.  
  
 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 Описывает указанном компьютере.  
  
 [METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 Описывает элемент массива в массиве.  
  
 [METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 Описывает адрес поля класса или структуры.  
  
 [METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 Описывает адрес локальной переменной в пределах области \(как правило, функции или метода\).  
  
 [METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 Описывает адрес метода класса.  
  
 [METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 Описывает параметр метода или функции.  
  
 [METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 Описывает возвращаемое значение метода или функции.  
  
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 Описывает тип поля принятый из метаданных.  
  
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)  
 Описывает указанный модуль \(DLL или EXE, сборку\).  
  
 [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 Описывает сведения о состоянии о путях поиска символов, которые были производится.  
  
 [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 Описывает собственный адрес.  
  
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 Описывает тип поля принятый от символов PDB.  
  
 [PENDING\_BP\_STATE\_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 Описывает состояние точки останова, готовы привязать к местоположению кода.  
  
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)  
 Описывает процесс.  
  
 [PROGRAM\_NODE\_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 Описывает список  IDebugProgramNode2 объекты, представляющие узлы программы.  
  
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 Описывает процессы, выполняющиеся на компьютере.  
  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 Описывает расположение линии и столбцов в заданный текст.  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 Описывает свойства потока.  
  
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)  
 Описывает вид поля.  
  
 [UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 Описывает физический адрес.  
  
 [UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 Описывает адрес, по отношению к a `this` указатель \(`Me` в Visual Basic\).  
  
## Требования  
 Заголовок: msdbg.h, sh.h или ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Справочник по интерфейсам API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)