---
title: "Интерфейсы поставщика символов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "интерфейсы, обработчик символов"
  - "Обработчик символов, интерфейсы"
  - "Обработчик символов, расчет значений переменных"
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Интерфейсы поставщика символов
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Следующие интерфейсы для обработки символ [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## Обсуждение  
 Эти интерфейсы используются для оценки стек при вызове переменных во время работы в режиме приостановки выполнения.  Они реализуются только для поставщиков символов среды CLR \(пакет обновления\).  
  
|Интерфейс|Реализуется определяемая|Описание|  
|---------------|------------------------------|--------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|ХП|Представляет адрес элемента.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|ХП|Представляет адрес элемента, предоставляя доступ к идентификатору процесса|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|ХП|Представляет символ массива или типа массива.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|ХП|Представляет символ или тип класса.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|ХП|Представляет поставщика символов COM\+ с методами, которые относятся к управляемому коду.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|ХП|Представляет поставщика символов COM\+ с методами, которые относятся к управляемому коду и расширяет IDebugComPlusSymbolProvider.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|ХП|Представляет символ или тип, который является контейнером для других символов или типов.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|ХП|Представляет настраиваемый атрибут, можно вложить в символ.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|ХП|Представляет запрос для настраиваемых атрибутов для метода или типа.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|ХП|Предоставляет доступ к настраиваемым атрибутам на символе.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|ХП|Базовый интерфейс для любого типа, который может быть определена во время выполнения.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|ХП|Представляет поля для динамического [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) объект.|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|ХП|Представляет тип перечисления.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Хп|Расширяет типы доступных полей в универсальные шаблоны управляемого кода поддержки.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|ХП|Базовый класс для всех полей; представляет описание символов или типа.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|ХП|Представляет определение поля для универсального типа управляемого кода.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|ХП|Представляет экземпляр поля для универсального типа управляемого кода.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|ХП|Представляет параметр универсального типа управляемого кода.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|ХП|Представляет метод.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|ХП|Представляет необязательный модификатор отладки.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|ХП|Представляет указатель.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|ХП|Представляет значение из перечисления примитивного типа IDebugField интерфейс.|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|ХП|Представляет свойство класса управляемого кода, который может быть возвращает или задает.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|ХП|Представляет поставщик, предоставляющий символы и типы символов.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|ХП|Представляет поставщика символов с прямым доступом к метаданным и интерфейсам символов.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|ХП|Представляет возможность создать поле, представляющее тип.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|ХП|Расширяет IDebugTypeFieldBuilder возможность создания типы массива.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|ХП|Представляет коллекцию объектов [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md).|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|ХП|Представляет коллекцию объектов [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md).|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|ХП|Представляет коллекцию объектов [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).|  
  
## См. также  
 [Справочник по интерфейсам API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)