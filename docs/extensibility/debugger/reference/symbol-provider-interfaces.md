---
title: Интерфейсы поставщика символов | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715840"
---
# <a name="symbol-provider-interfaces"></a>Интерфейсы поставщика символов
Ниже приведены интерфейсы обработки символов для [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] .

## <a name="discussion"></a>Разговор
 Эти интерфейсы используются для вычисления переменных в стеке вызовов в режиме приостановки выполнения. Они реализуются только для поставщиков символов общеязыковой среды выполнения (SP).

|Интерфейс|Реализовано|Описание:|
|---------------|--------------------|-----------------|
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Представляет адрес элемента.|
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Представляет адрес элемента, предоставляющий доступ к ИДЕНТИФИКАТОРу процесса.|
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Представляет символ массива или тип массива.|
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Представляет символ класса или тип класса.|
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Представляет поставщик символов COM+ с методами, характерными для управляемого кода.|
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Представляет поставщик символов COM+ с методами, специфичными для управляемого кода, и расширяет **идебугкомплуссимболпровидер**.|
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Представляет символ или тип, являющийся контейнером для других символов или типов.|
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Представляет настраиваемый атрибут, который можно присоединить к символу.|
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Представляет запрос для настраиваемых атрибутов метода или типа.|
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Предоставляет доступ к настраиваемым атрибутам символа.|
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Базовый интерфейс для любого типа, который может быть определен во время выполнения.|
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Представляет динамическое поле для объекта [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md) .|
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Представляет тип перечисления.|
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Портов|Расширяет типы доступных полей для поддержки универсальных типов управляемого кода.|
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Базовый класс для всех полей; представляет описание символа или типа.|
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Представляет определение поля для универсального типа управляемого кода.|
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Представляет экземпляр поля для универсального типа управляемого кода.|
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Представляет параметр для универсального типа управляемого кода.|
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Представляет метод.|
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Представляет необязательный модификатор отладки.|
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Представляет указатель.|
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Представляет значение перечисления типа-примитива из интерфейса [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) .|
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Представляет свойство управляемого класса кода, которое может быть получено или задано.|
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Представляет поставщик символов, предоставляющий символы и типы.|
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Представляет поставщик символов с прямым доступом к метаданным и основным интерфейсам символов.|
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Представляет возможность создания поля, представляющего тип.|
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Расширяет **идебугтипефиелдбуилдер** , чтобы иметь возможность создавать типы массивов.|
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Представляет коллекцию объектов [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) .|
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Представляет коллекцию объектов [идебугкустоматтрибуте](../../../extensibility/debugger/reference/idebugcustomattribute.md) .|
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Представляет коллекцию объектов [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) .|

## <a name="see-also"></a>См. также
- [Справочник по интерфейсам API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
