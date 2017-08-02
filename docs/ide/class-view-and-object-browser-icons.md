---
title: "Значки представления классов и обозревателя объектов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Значки представления классов и обозревателя объектов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В **представлении классов** и **обозревателе объектов** отображаются значки, служащие для представления сущностей кода, таких как пространства имен, классы, функции и переменные.  В следующей таблице приведены значки с их описанием.  
  
|Значок|Описание|Значок|Описание|  
|------------|--------------|------------|--------------|  
|![Символ пространства имен](~/docs/ide/media/vxnamespace_icon.gif "vxNamespace\_Icon")|Пространство имен|![Символ объявления](~/docs/ide/media/vxmethod_icon.gif "vxMethod\_Icon")|Метод или функция|  
|![Значок класса](~/docs/ide/media/vxclass_icon.gif "vxClass\_Icon")|Класс|![Символ оператора](~/docs/ide/media/vxoperator_icon.gif "vxOperator\_Icon")|Оператор|  
|![Символ интерфейса без описания операций](~/docs/ide/media/vxinterface_icon.gif "vxInterface\_Icon")|Интерфейс|![Символ свойства](~/docs/ide/media/vxproperty_icon.gif "vxProperty\_Icon")|Свойство.|  
|![Символ структуры](~/docs/ide/media/vxstruct_icon.gif "vxStruct\_Icon")|Структура|![Значок поля](~/docs/ide/media/vxfield_icon.gif "vxField\_Icon")|Поле или переменная|  
|![Символ объединения](~/docs/ide/media/vxunion_icon.gif "vxUnion\_Icon")|Union|![Символ события](~/docs/ide/media/vxevent_icon.gif "vxEvent\_Icon")|Событие|  
|![Символ перечисления](~/docs/ide/media/vxenum_icon.gif "vxEnum\_Icon")|Enum|![Значок константы](~/docs/ide/media/vxconstant_icon.gif "vxConstant\_Icon")|Константа|  
|![Символ определения типа](~/docs/ide/media/vxtypedef_icon.gif "vxTypeDef\_Icon")|TypeDef|![Символ элемента перечисления](~/docs/ide/media/vxenumitem_icon.gif "vxEnumItem\_Icon")|Элемент перечисления|  
|![Символ модуля Visual Studio](~/docs/ide/media/vxmodule_icon.gif "vxModule\_Icon")|Модуль|![Символ элемента сопоставления](~/docs/ide/media/vxmapitem_icon.gif "vxMapItem\_Icon")|Элемент сопоставления|  
|![Символ метода расширения](~/docs/ide/media/extensionmethod.gif "ExtensionMethod")|Метод расширения|![Символ объявления](~/docs/ide/media/vxmethod_icon.gif "vxMethod\_Icon")|Внешнее объявление|  
|![Символ делегата](~/docs/ide/media/vxdelegate_icon.gif "vxDelegate\_Icon")|Делегат|![Значок ошибки представления классов и обозревателя объектов](~/docs/ide/media/erroricon.gif "ErrorIcon")|Ошибка|  
|![Символ исключения](~/docs/ide/media/vxexception_icon.gif "vxException\_Icon")|Исключение|![Символ шаблона](~/docs/ide/media/vxtemplate_icon.gif "vxTemplate\_Icon")|Шаблон|  
|![Символ сопоставления](~/docs/ide/media/vxmap_icon.gif "vxMap\_Icon")|Сопоставление|![Символ восклицательного знака при ошибке](~/docs/ide/media/vxerror_icon.gif "vxError\_Icon")|Нет данных|  
|![Символ пересылки типов](~/docs/ide/media/ob_type_forward.gif "ob\_type\_forward")|Пересылка типов|||  
  
## Сигнальные значки  
 Следующие сигнальные значки применимы ко всем перечисленным выше значкам и указывают на их доступность.  
  
> [!NOTE]
>  Если проект включен в базу данных системы управления версиями, могут отображаться дополнительные сигнальные значки, указывающие на состояние объекта в системе управления версиями, например, извлечен или возвращен.  
  
|Значок|Описание|  
|------------|--------------|  
|\<Сигнальный значок отсутствует\>|Public.  доступен из любого места в компоненте и из любого компонента, который содержит на него ссылку.|  
|![Символ Protected](~/docs/ide/media/vxsignal_icon_key.gif "vxSignal\_Icon\_Key")|Защищенный —  доступен из содержащего класса или типа или из класса или типа, которые являются производными от содержащего класса или типа.|  
|![Символ Private](~/docs/ide/media/vxsignal_icon_lock.gif "vxSignal\_Icon\_Lock")|Закрытый —  доступен только из содержащего класса или типа.|  
|![Символ Sealed](~/docs/ide/media/vxsignal_icon_envelope.gif "vxSignal\_Icon\_Envelope")|Запечатанным.|  
|![Символ Friend&#47;Internal](~/docs/ide/media/vxsignal_icon_diamond.gif "vxSignal\_Icon\_Diamond")|Дружественный и внутренний.  доступен только из проекта.|  
|![Значок стрелки](~/docs/ide/media/vxsignal_icon_arrow.gif "vxSignal\_Icon\_Arrow")|Ярлык —  ярлык объекта.|  
  
## См. также  
 [Просмотр структуры кода](../ide/viewing-the-structure-of-code.md)