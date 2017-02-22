---
title: "Значки представления классов и обозревателя объектов | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "значки, в обозревателе объектов"
  - "сигнальные значки"
  - "Средство представления классов, символы"
  - "графические символы"
  - "IntelliSense, значки"
  - "значки, IntelliSense"
  - "символы, значки обозревателя объектов"
  - "Обозреватель объектов, значки в представлении классов"
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Значки представления классов и обозревателя объектов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В **представлении классов** и **обозревателе объектов** отображаются значки, служащие для представления сущностей кода, таких как пространства имен, классы, функции и переменные.  В следующей таблице приведены значки с их описанием.  
  
|Значок|Описание|Значок|Описание|  
|------------|--------------|------------|--------------|  
|![Символ пространства имен](../ide/media/vxnamespace_icon.gif "vxNamespace\_Icon")|Пространство имен|![Символ объявления](../ide/media/vxmethod_icon.png "vxMethod\_Icon")|Метод или функция|  
|![Значок класса](../ide/media/vxclass_icon.png "vxClass\_Icon")|Класс|![Символ оператора](../ide/media/vxoperator_icon.png "vxOperator\_Icon")|Оператор|  
|![Символ интерфейса без описания операций](../ide/media/vxinterface_icon.png "vxInterface\_Icon")|Интерфейс|![Символ свойства](../ide/media/vxproperty_icon.png "vxProperty\_Icon")|Свойство.|  
|![Символ структуры](../ide/media/vxstruct_icon.png "vxStruct\_Icon")|Структура|![Значок поля](../ide/media/vxfield_icon.png "vxField\_Icon")|Поле или переменная|  
|![Символ объединения](../ide/media/vxunion_icon.png "vxUnion\_Icon")|Union|![Символ события](../ide/media/vxevent_icon.png "vxEvent\_Icon")|Событие|  
|![Символ перечисления](../ide/media/vxenum_icon.png "vxEnum\_Icon")|Enum|![Значок константы](../ide/media/vxconstant_icon.png "vxConstant\_Icon")|Константа|  
|![Символ определения типа](../ide/media/vxtypedef_icon.png "vxTypeDef\_Icon")|TypeDef|![Символ элемента перечисления](../ide/media/vxenumitem_icon.png "vxEnumItem\_Icon")|Элемент перечисления|  
|![Символ модуля Visual Studio](../ide/media/vxmodule_icon.gif "vxModule\_Icon")|Модуль|![Символ элемента сопоставления](../ide/media/vxmapitem_icon.png "vxMapItem\_Icon")|Элемент сопоставления|  
|![Символ метода расширения](../ide/media/extensionmethod.png "ExtensionMethod")|Метод расширения|![Символ объявления](../ide/media/vxmethod_icon.png "vxMethod\_Icon")|Внешнее объявление|  
|![Символ делегата](../ide/media/vxdelegate_icon.png "vxDelegate\_Icon")|Делегат|![Значок ошибки представления классов и обозревателя объектов](../ide/media/erroricon.png "ErrorIcon")|Ошибка|  
|![Символ исключения](../ide/media/vxexception_icon.png "vxException\_Icon")|Исключение|![Символ шаблона](../ide/media/vxtemplate_icon.png "vxTemplate\_Icon")|Шаблон|  
|![Символ сопоставления](../ide/media/vxmap_icon.png "vxMap\_Icon")|Сопоставление|![Символ восклицательного знака при ошибке](../ide/media/vxerror_icon.png "vxError\_Icon")|Нет данных|  
|![Символ пересылки типов](../ide/media/ob_type_forward.png "ob\_type\_forward")|Пересылка типов|||  
  
## Сигнальные значки  
 Следующие сигнальные значки применимы ко всем перечисленным выше значкам и указывают на их доступность.  
  
> [!NOTE]
>  Если проект включен в базу данных системы управления версиями, могут отображаться дополнительные сигнальные значки, указывающие на состояние объекта в системе управления версиями, например, извлечен или возвращен.  
  
|Значок|Описание|  
|------------|--------------|  
|\<Сигнальный значок отсутствует\>|Public.  доступен из любого места в компоненте и из любого компонента, который содержит на него ссылку.|  
|![Символ Protected](../ide/media/vxsignal_icon_key.png "vxSignal\_Icon\_Key")|Защищенный —  доступен из содержащего класса или типа или из класса или типа, которые являются производными от содержащего класса или типа.|  
|![Символ Private](../ide/media/vxsignal_icon_lock.png "vxSignal\_Icon\_Lock")|Закрытый —  доступен только из содержащего класса или типа.|  
|![Символ Sealed](../ide/media/vxsignal_icon_envelope.png "vxSignal\_Icon\_Envelope")|Запечатанным.|  
|![Символ Friend&#47;Internal](../ide/media/vxsignal_icon_diamond.png "vxSignal\_Icon\_Diamond")|Дружественный и внутренний.  доступен только из проекта.|  
|![Значок стрелки](../ide/media/vxsignal_icon_arrow.gif "vxSignal\_Icon\_Arrow")|Ярлык —  ярлык объекта.|  
  
## См. также  
 [Просмотр структуры кода](../ide/viewing-the-structure-of-code.md)