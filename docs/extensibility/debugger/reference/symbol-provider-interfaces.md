---
title: Интерфейсы поставщика символов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 908e597d9ee0a1db4e78de02f3dd4ade1a9aa119
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945363"
---
# <a name="symbol-provider-interfaces"></a>Интерфейсы поставщика символов
Ниже перечислены интерфейсы обработки символов для [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="discussion"></a>Обсуждение  
 Эти интерфейсы используются для оценки переменных в стеке вызовов в режиме приостановки выполнения. Они реализуются только для общих поставщиков символ среды выполнения языка (SP).  
  
|Интерфейс|Реализуется|Описание:|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Представляет адрес элемента.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Представляет собой адрес элемента, предоставление доступа к идентификатор процесса.|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Представляет тип массива или массива символов.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Представляет символ класс или тип класса.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Представляет поставщик символов COM + с методами, характерные для управляемого кода.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Представляет поставщик символов COM + с методами, которые относятся к управляемому коду и расширяет **IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Представляет символ или тип, который является контейнером для других символов или типов.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Представляет пользовательский атрибут, который может быть присоединен к символа.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Представляет запрос для настраиваемых атрибутов для метода или типа.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Предоставляет доступ к настраиваемые атрибуты в символ.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Базовый интерфейс для любого типа, который можно определить во время выполнения.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Представляет динамическое поле для [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) объекта.|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Представляет тип перечисления.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP|Расширяет типы доступных полей для поддержки универсальных типов в управляемом коде.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Базовый класс для всех полей; Представляет описание символа или тип.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Представляет определение поля для универсального типа управляемого кода.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Представляет экземпляр поля для универсального типа управляемого кода.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Представляет параметр универсального типа управляемого кода.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Представляет метод.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Представляет необязательный модификатор отладки.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Представляет указатель.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Представляет значение примитивного типа перечисления из [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс.|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Представляет свойство класса управляемого кода, который можно получить или задать.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Представляет поставщик символов, который предоставляет типы и символы.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Представляет поставщика символов с прямым доступом к интерфейсам символ метаданных и core.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Представляет возможность создавать поле, которое представляет тип.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Расширяет **IDebugTypeFieldBuilder** чтобы иметь возможность создавать типы массивов.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Представляет коллекцию [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объектов.|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Представляет коллекцию [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) объектов.|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Представляет коллекцию [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объектов.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)