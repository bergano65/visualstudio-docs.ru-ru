---
title: Значки представления классов и обозревателя объектов | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f0a4371ae086e158f3fd7025e9867ffb99c92090
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="class-view-and-object-browser-icons"></a>Значки представления классов и обозревателя объектов

**Представление классов** и **обозреватель объектов** отображают значки, представляющие сущности кода, например пространства имен, классы, функции и переменные. Эти значки описаны в приведенной ниже таблице.

|Значок|Описание:|Значок|Описание:|
|----------|-----------------|----------|-----------------|
|![Символ пространства имен](../ide/media/vxnamespace_icon.gif "vxNamespace_Icon")|Пространство имен|![Символ объявления](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|Метод или функция|
|![Значок класса](../ide/media/vxclass_icon.gif "vxClass_Icon")|Класс|![Символ оператора](../ide/media/vxoperator_icon.gif "vxOperator_Icon")|Оператор|  
|![Символ интерфейса без описания операций](../ide/media/vxinterface_icon.gif "vxInterface_Icon")|Интерфейс|![Символ свойства](../ide/media/vxproperty_icon.gif "vxProperty_Icon")|Свойство.|
|![Символ структуры](../ide/media/vxstruct_icon.gif "vxStruct_Icon")|Структура|![Значок поля](../ide/media/vxfield_icon.gif "vxField_Icon")|Поле или переменная|  
|![Символ объединения](../ide/media/vxunion_icon.gif "vxUnion_Icon")|Объединение|![Символ события](../ide/media/vxevent_icon.gif "vxEvent_Icon")|событие|  
|![Символ перечисления](../ide/media/vxenum_icon.gif "vxEnum_Icon")|Enum|![Значок константы](../ide/media/vxconstant_icon.gif "vxConstant_Icon")|Константа|  
|![Символ определения типа](../ide/media/vxtypedef_icon.gif "vxTypeDef_Icon")|TypeDef|![Символ элемента перечисления](../ide/media/vxenumitem_icon.gif "vxEnumItem_Icon")|Элемент перечисления|  
|![Символ модуля Visual Studio](../ide/media/vxmodule_icon.gif "vxModule_Icon")|Module|![Символ элемента сопоставления](../ide/media/vxmapitem_icon.gif "vxMapItem_Icon")|Элемент сопоставления|  
|![Символ метода расширения](../ide/media/extensionmethod.gif "ExtensionMethod")|Метод расширения|![Символ объявления](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|Внешнее объявление|  
|![Символ делегата](../ide/media/vxdelegate_icon.gif "vxDelegate_Icon")|делегат|![Значок ошибки для представления классов и обозревателя объектов](../ide/media/erroricon.gif "ErrorIcon")|Error|  
|![Символ исключения](../ide/media/vxexception_icon.gif "vxException_Icon")|Исключение|![Символ шаблона](../ide/media/vxtemplate_icon.gif "vxTemplate_Icon")|Шаблон|  
|![Символ сопоставления](../ide/media/vxmap_icon.gif "vxMap_Icon")|Карта|![Символ восклицательного знака при ошибке](../ide/media/vxerror_icon.gif "vxError_Icon")|Неизвестно|  
|![Символ перенаправления типов](../ide/media/ob_type_forward.gif "ob_type_forward")|Перенаправление типов|||  

## <a name="signal-icons"></a>Сигнальные значки

Приведенные ниже сигнальные значки применяются ко всем перечисленным выше значкам и указывают их доступность.

|Значок|Описание:|
|----------|-----------------|  
|\<Без сигнального значка>|Общедоступный. Доступен из любой части этого компонента, а также из любого компонента, который на него ссылается.|  
|![Сигнальный символ "Защищенный"](../ide/media/vxsignal_icon_key.gif "vxSignal_Icon_Key")|Защищенный. Доступен из содержащего класса или типа, а также из производных от них классов и типов.|  
|![Сигнальный символ "Закрытый"](../ide/media/vxsignal_icon_lock.gif "vxSignal_Icon_Lock")|Закрытый. Доступен только в содержащем классе или типе.|  
|![Сигнальный символ "Запечатанный"](../ide/media/vxsignal_icon_envelope.gif "vxSignal_Icon_Envelope")|Запечатанный.|  
|![Сигнальный символ "Дружественный&#47;внутренний"](../ide/media/vxsignal_icon_diamond.gif "vxSignal_Icon_Diamond")|Дружественный/внутренний. Доступен только из проекта.|  
|![Сигнальный символ "Стрелка"](../ide/media/vxsignal_icon_arrow.gif "vxSignal_Icon_Arrow")|Ярлык. Ярлык объекта.|

> [!NOTE]
> Если ваш проект включен в базу данных управления версиями, могут отображаться дополнительные сигнальные значки, указывающие состояние управления версиями, например, возвращено или извлечено.

## <a name="see-also"></a>См. также

[Просмотр структуры кода](../ide/viewing-the-structure-of-code.md)