---
title: Структуры и объединения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e0ef171d24b3744657a2cb05338b2b124a6331c9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56692532"
---
# <a name="structures-and-unions"></a>Структуры и объединения
Ниже приведены структуры и объединения в Visual Studio отладку SDK.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) указывает идентификатор процесса, который может быть системный идентификатор или GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) описывает условия, при которых точка останова будет срабатывать.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) описывает разрешение точки останова ошибки, включая расположение, программы и потока.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) указывает тип структуры, используемые для описания расположения точки останова.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) определяет компоненты, которые описывают расположение точки останова по адресу в коде.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) описывает расположение точки останова, которая привязано непосредственно к адресу в отлаживаемой программы.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) описывает расположение точки останова в строке в файле исходного кода.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) описывает смещения расположение точки останова в функцию в коде.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) используется для установки точек останова кода на основе строки, пользователь может ввести в интегрированной среде разработки.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) используется для задания точки останова по данным, которые основаны на строку, пользователь может ввести в интегрированной среде разработки.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) описывает разрешение точку останова в определенном месте.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) описывает число и условия, от которых будет запускаться точку останова после был передан ранее.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) содержит сведения, необходимые для реализации точки останова.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) содержит сведения, необходимые для реализации точку останова (то же, что [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) структуру, но содержит сведения о поставщике GUID "," ограничение "и" точка трассировки).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) описывает расположение точки останова в коде.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) описывает результат привязки точки останова по данным.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) описывает информацию связанная точка останова для кода точки останова или точки останова по данным.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) задает структуру разрешения расположения точки останова.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) описывает массив строк.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) указывает сведения о типом поля, взятое из метаданных.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) описывает вызов функции или метода.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) описание компьютера, на котором выполняется отладчик.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) описывает список идентификаторов GUID.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) описывает контекст памяти или контекст кода.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) описывает адреса в отлаживаемой программы.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) представляет собой одну из нескольких различных видов адресов.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) идентифицирует пользовательское средство просмотра или тип визуализатора.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) описывает свойство отладки, в свою очередь, описывающий объект иерархическую сущность, которая имеет имя, тип и значение.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) описывает ссылку.

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) описывает Дизассемблированный код в интегрированную среду разработки для отображения.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) описывает ошибку исключения или во время выполнения, выводится отлаживаемой программы.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) описывает локальную переменную, параметр или другое поле.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) описывает кадр стека.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) описывает массив уникальных идентификаторов для доступных отладчиков.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) используется для задания данных JustMyCode для модуля.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) описывает конкретного компьютера.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) описывает элемент массива в массив.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) описывает адрес поля класса или структуры.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) описывает адрес локальной переменной в области (обычно функцию или метод).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) описывает адрес методу класса.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) описывает параметр метода или функции.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) описывает возвращаемое значение из метода или функции.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) описывает тип поля, взятое из метаданных.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) описывает определенного модуля (DLL, EXE-файла или сборки).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) описывает сведения о пути поиска символов, которые после состоянии.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) описывает собственный адрес.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) описывает тип поля, взятое из PDB-символов.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) описывает состояние точки останова, которая готова для привязки к расположение кода.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) описывается процесс.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) описывается список [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объекты, представляющие узлы программы.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Описывает процессы, запущенные на компьютере.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) описывает положение строки и столбца в заданный текст.

- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) описаны свойства потока.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) описывает тип поля.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) описывает физический адрес.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) описывает адрес, который задается по отношению к `this` указатель (`Me` в Visual Basic).

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h sh.h и ee.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Справочник по интерфейсам API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)