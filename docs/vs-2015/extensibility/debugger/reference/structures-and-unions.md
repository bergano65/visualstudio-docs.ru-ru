---
title: Структуры и объединения | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 374ee61c65da830b85a8983e61939c25c2296718
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227114"
---
# <a name="structures-and-unions"></a>Структуры и объединения
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ниже приведены структуры и объединения в Visual Studio отладку SDK.  
  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 Указывает идентификатор процесса, который может быть системный идентификатор или GUID.  
  
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 Описывает условия, при которых точка останова будет срабатывать.  
  
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 Описание разрешения ошибки точки останова, включая расположение, программы и потока.  
  
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 Указывает тип структуры, используемые для описания расположения точки останова.  
  
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 Определяет компоненты, которые описывают расположение точки останова по адресу в коде.  
  
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 Описывает расположение точки останова, которая привязано непосредственно к адресу в отлаживаемой программы.  
  
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 Описывает расположение точки останова в строке в файле исходного кода.  
  
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 Описывает смещения расположение точки останова в функцию в коде.  
  
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 Используется для установки точек останова кода на основе строки, пользователь может ввести в интегрированной среде разработки.  
  
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 Используется для задания точки останова по данным, которые основаны на строку, пользователь может ввести в интегрированной среде разработки.  
  
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 Описывает разрешение точку останова в определенном месте.  
  
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 Описывает число и условия, от которых будет запускаться точку останова после был передан ранее.  
  
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 Содержит сведения, необходимые для реализации точки останова.  
  
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 Содержит сведения, необходимые для реализации точку останова (то же, что [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) структуру, но содержит сведения о поставщике GUID "," ограничение "и" точка трассировки).  
  
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 Описывает расположение точки останова в коде.  
  
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 Описывает результат привязки точки останова по данным.  
  
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 Описывает информацию связанная точка останова для кода точки останова или точки останова по данным.  
  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 Задает структуру разрешения расположения точки останова.  
  
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 Описывает массив строк.  
  
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 Указывает сведения о типом поля, взятое из метаданных.  
  
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)  
 Описывает вызов функции или метода.  
  
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 Описание компьютера, на котором выполняется отладчик.  
  
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 Описывает список идентификаторов GUID.  
  
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)  
 Описывает контекст памяти или контекст кода.  
  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 Описывает адрес в отлаживаемой программы.  
  
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 Представляет собой одну из нескольких различных видов адресов.  
  
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 Определяет пользовательское средство просмотра или введите визуализатора.  
  
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 Описывает свойство отладки, в свою очередь, описывающий объект иерархическую сущность, которая имеет имя, тип и значение.  
  
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 Описывает ссылку.  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 Описывает Дизассемблированный код в интегрированную среду разработки для отображения.  
  
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 Описывает исключение или ошибка времени выполнения, выводится отлаживаемой программы.  
  
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)  
 Описывает локальную переменную, параметр или другое поле.  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 Описывает кадр стека.  
  
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 Описывает массив уникальных идентификаторов для доступных отладчиков.  
  
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 Используется для задания данных JustMyCode для модуля.  
  
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 Описание конкретного компьютера.  
  
 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 Описывает элемент массива в массив.  
  
 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 Описывает адрес поля класса или структуры.  
  
 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 Описывает адрес локальной переменной в области (обычно функцию или метод).  
  
 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 Описывает адрес метода класса.  
  
 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 Описывает параметр метода или функции.  
  
 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 Описывает возвращаемое значение из метода или функции.  
  
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 Описывает тип поля, взятое из метаданных.  
  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)  
 Описание определенного модуля (DLL, EXE-файла или сборки).  
  
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 Описывает сведения о пути поиска символов, которые после состоянии.  
  
 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 Описывает собственный адрес.  
  
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 Описывает тип поля, взятое из PDB-символов.  
  
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 Описывает состояние точки останова, которая готова для привязки к расположение кода.  
  
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)  
 Описывает процесс.  
  
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 Описывается список [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объекты, представляющие узлы программы.  
  
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 Описывает процессы, запущенные на компьютере.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 Описывает расположение строк и столбцов в данном тексте.  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 Описывает свойства потока.  
  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)  
 Описание типа поля.  
  
 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 Описывает физический адрес.  
  
 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 Описывает адрес, который задается по отношению к `this` указатель (`Me` в Visual Basic).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h sh.h и ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)

