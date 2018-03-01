---
title: "Структур и объединений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1cae50d4ff122ebea1fa11291570ac23f556f6f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="structures-and-unions"></a>Структур и объединений
Ниже приведены структур и объединений в Visual Studio пакет SDK для отладки.  
  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 Указывает идентификатор процесса, который может быть системный идентификатор или GUID.  
  
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 Описывает условия, при которых точка останова будет срабатывать.  
  
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 Описание разрешения ошибки точки останова, включая расположение, программы и поток.  
  
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 Указывает тип структуры, используемый для описания расположение точки останова.  
  
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 Определяет компоненты, которые описывают расположение точки останова по адресу в коде.  
  
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 Описывает местоположение точки останова, привязано непосредственно к адрес из отлаживаемой программы.  
  
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 Описывает расположение точки останова в строке в файле исходного кода.  
  
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 Описывает смещения расположение точки останова в функции в коде.  
  
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 Используется для установки точек останова кода на основе строки, пользователь может ввести в интегрированной среде разработки.  
  
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 Используется для задания точки останова в данных, основанных на строку, пользователь может ввести в интегрированной среде разработки.  
  
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 Описание разрешения точки останова в определенном месте.  
  
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 Описывает количество и условия, от которых точка останова срабатывает после ранее успешно.  
  
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 Содержит сведения, необходимые для реализации точки останова.  
  
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 Содержит сведения, необходимые для реализации точки останова (то же, что [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) структуру, но содержит сведения о поставщике GUID, ограничения и точки трассировки).  
  
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 Описывает расположение точки останова в коде.  
  
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 Описывает результат привязки точки останова по данным.  
  
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 Описывает связанная точка останова сведения о коде точки останова или точки останова по данным.  
  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 Определяет структуру разрешения расположения точки останова.  
  
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 Описывает массив строк.  
  
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 Указывает сведения о типе поля берутся из метаданных.  
  
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)  
 Описывает вызов функции или метода.  
  
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 Описывает компьютер, на котором выполняется отладчик.  
  
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 Описывает список идентификаторов GUID.  
  
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)  
 Описывает контекст памяти или контекст кода.  
  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 Описывает адрес из отлаживаемой программы.  
  
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 Представляет одно из множества различных видов адресов.  
  
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 Определяет пользовательское средство просмотра или введите визуализатора.  
  
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 Описывает отладочное свойство, в свою очередь, описывает объект иерархический характер, который имеет имя, тип и значение.  
  
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 Описывает ссылку.  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 Описывает Дизассемблированный код в интегрированную среду разработки для отображения.  
  
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 Описывает исключения или ошибки во время выполнения вызванных отлаживаемой программы.  
  
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)  
 Описывает локальную переменную, параметр или другое поле.  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 Описывает кадр стека.  
  
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 Описывает массив уникальных идентификаторов для Доступные отладчики.  
  
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 Используется для задания сведений JustMyCode для модуля.  
  
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 Описывает конкретного компьютера.  
  
 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 Описывает элемент массива в массиве.  
  
 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 Описывает адрес поля класса или структуры.  
  
 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 Описывает адрес локальной переменной в области (обычно функция или метод).  
  
 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 Описывает адрес методу класса.  
  
 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 Описывает параметр метода или функции.  
  
 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 Описывает значение, возвращаемое из метода или функции.  
  
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 Описывает тип поля, берутся из метаданных.  
  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)  
 Описание определенного модуля (DLL, EXE-файла или сборки).  
  
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 Описание состояния сведения о пути поиска символов, которые был выполнен поиск.  
  
 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 Описывает собственного адреса.  
  
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 Описывает тип поля, взяты из PDB-символов.  
  
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 Описывает состояние точки останова, можно привязать расположение кода.  
  
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)  
 Описывает процесс.  
  
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 Описывается список [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объекты, представляющие узлы программы.  
  
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 Описывает процессы, запущенные на компьютере.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 Описывает расположение строк и столбцов в заданном тексте.  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 Описание свойств потока.  
  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)  
 Описание типа поля.  
  
 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 Описывает физические адреса.  
  
 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 Описывает адрес, который определяется относительно `this` указателя (`Me` в Visual Basic).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h, sh.h или ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)