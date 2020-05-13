---
title: Структуры и союзы Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19d8f547d98488edffc6049be7619e5b5e921d93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713496"
---
# <a name="structures-and-unions"></a>Структуры и объединения
Ниже приведены структуры и союзы в Visual Studio Debugging SDK.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Упоняет идентификатор процесса, который может быть либо идентификатором системы, либо GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Описывает условия, при которых будет гореть точка разрыва.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Описывает разрешение точки разрыва ошибки, включая местоположение, программу и поток.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Определяет тип структуры, используемой для описания местоположения точки разрыва.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Определяет компоненты, описывающие местоположение точки разрыва по адресу в коде.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Описывает расположение точки разрыва, которая привязана непосредственно к отладке программы.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Описывает расположение точки разрыва в строке в исходном файле кода.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Описывает офсетное расположение точки разрыва в функции в коде.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Используется для настройки точек разрыва кода на основе строки, которую пользователь может ввести из IDE.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Используется для настройки точек разрыва данных, основанных на строке, которую пользователь может ввести из IDE.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Описывает разрешение точки разрыва в определенном месте.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Описывает количество и условия, при которых точка разрыва будет уволена после того, как была ранее пройдена.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Содержит информацию, необходимую для реализации точки разрыва.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Содержит информацию, необходимую для реализации точки разрыва (так же, как [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) структуру, но включает в себя информацию о GUID поставщиках, ограничениях и информации о точках трассировки).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Описывает расположение точки разрыва кода.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Описывает результат связывания точки разрыва данных.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Описывает информацию о связанной точке разрыва для точки разрыва кода или точки разрыва данных.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Определяет структуру расположения разрешения точки разрыва.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Описывает массив строк.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Определяет информацию о типе поля, взятом из метаданных.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Описывает вызов к функции или методу.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) Описывает компьютер, на котором работает отладчик.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) Описывает список GUID.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Описывает контекст памяти или контекст кода.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Описывает адрес в отладке программы.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Представляет один из нескольких различных видов адресов.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Идентифицирует пользовательского просмотра или ввизуализатор типа.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Описывает свойство отладки, которое, в свою очередь, описывает объект иерархического характера, который имеет имя, тип и значение.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Описывает ссылку.

- [РазборкаДанные](../../../extensibility/debugger/reference/disassemblydata.md) Описывает разборку в IDE для отображения.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Описывает исключение или ошибку времени выполнения, брошенную отладкой программы.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Описывает локальную переменную, параметр или другое поле.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Описывает кадр стека.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) Описывает массив уникальных идентификаторов для доступных отладок двигателей.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Используется для настройки информации JustMyCode для модуля.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Описывает конкретную машину.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Описывает элемент массива в массиве.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Описывает адрес поля класса или структуры.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Описывает адрес локальной переменной в пределах области (обычно функция или метод).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Описывает адрес метода класса.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Описывает параметр метода или функции.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Описывает значение возврата от метода или функции.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Описывает тип поля, взятый из метаданных.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Описывает определенный модуль (DLL, EXE или сборка).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) Описывает информацию о состоянии поиска символов, которые были поисковые.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Описывает родной адрес.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Описывает тип поля, взятый из символа PDB.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Описывает состояние точки разрыва, которая готова привязаться к местоположению кода.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Описывает процесс.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) Описывает список объектов [IDebugProgramNode2,](../../../extensibility/debugger/reference/idebugprogramnode2.md) представляющих узлы программы.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Описывает процессы, работающие на машине.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Описывает расположение строки и столбца в данном тексте.

- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) Описывает свойства потока.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Описывает тип поля.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Описывает физический адрес.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Описывает адрес, который по `this` отношению`Me` к указателю (в Visual Basic).

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h, sh.h, или ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Справка по API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
