---
title: Интерфейсы поставщика символов Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7929ba36c76f0db1cabab087afe3590de509efff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715840"
---
# <a name="symbol-provider-interfaces"></a>Интерфейсы поставщика символов
Ниже приведены интерфейсы обработки [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]символов для .

## <a name="discussion"></a>Обсуждение
 Эти интерфейсы используются для оценки переменных в стеке вызовов во время перерыва. Они реализуются только для поставщиков символов общего времени выполнения языка (SP).

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Представляет адрес элемента.|
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Представляет адрес элемента, обеспечивающий доступ к идентификатору процесса.|
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Представляет символ или тип массива массива.|
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Представляет символ класса или тип класса.|
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Представляет поставщика символов КОМЗ с методами, специфичными для управляемого кода.|
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Представляет поставщика символов КОМЗ с методами, которые специфичны для управляемого кода и расширяет **IDebugComPlusSymbolProvider.**|
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Представляет символ или тип, который является контейнером для других символов или типов.|
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Представляет пользовательский атрибут, который может быть прикреплен к символу.|
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Представляет запрос для пользовательских атрибутов на методе или типе.|
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Предоставляет доступ к пользовательским атрибутам на символе.|
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Базовый интерфейс для любого типа, который может быть определен во время выполнения.|
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Представляет динамическое поле для объекта [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)|
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Представляет тип перечисления.|
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Sp|Расширяет типы доступных полей для поддержки генериков управляемых кодов.|
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Базовый класс для всех полей; представляет описание символа или типа.|
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Представляет определение поля для общего типа управляемого кода.|
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Представляет экземпляр поля для общего типа управляемого кода.|
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Представляет собой параметр для общего типа управляемого кода.|
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Представляет метод.|
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Представляет собой отладку опциональном модификатором.|
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Представляет указатель.|
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Представляет собой примитивное значение перечисления типа из интерфейса [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)|
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Представляет свойство управляемого класса кода, который можно получить или установить.|
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Представляет поставщика символов, который предоставляет символы и типы.|
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Представляет поставщика символов с прямым доступом к метаданным и интерфейсам основных символов.|
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Представляет возможность создания поля, представляющего тип.|
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Расширяет **IDebugTypeFieldBuilder,** чтобы иметь возможность создавать типы массивов.|
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Представляет коллекцию объектов [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)|
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Представляет коллекцию объектов [IDebugCustomAttribute.](../../../extensibility/debugger/reference/idebugcustomattribute.md)|
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Представляет коллекцию объектов [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)|

## <a name="see-also"></a>См. также
- [Справка по API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
