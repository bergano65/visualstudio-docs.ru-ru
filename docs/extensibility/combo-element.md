---
title: Элемент поля со списком | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9759acc597d9a13ed084bdb8111cdd268a80bbc1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965657"
---
# <a name="combo-element"></a>Элемент поля со списком
Определяет команды, которые отображаются в поле со списком. Существует четыре вида со списком, следующим образом: DropDownCombo, DynamicCombo, IndexCombo и MRUCombo.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml 
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|guid|Обязательный. Идентификатор GUID идентификатора GUID и идентификатора команды.|  
|id|Обязательный. Идентификатор GUID и идентификатора идентификатор команды.|  
|defaultWidth|Обязательный. Целое число, указывающее ширину точек для поля со списком.|  
|idCommandList|Обязательный. Идентификатор, который отправляется в целевой объект активной команды для получения списка элементов, отображаемых в поле со списком. Идентификатор будет находиться в той же области GUID, что элемент управления.|  
|priority|Необязательный параметр. Числовое значение, указывающее приоритет.|  
|type|Необязательный параметр. Значение перечисления, которое указывает тип кнопки.<br /><br /> Если не указан, используется кнопка.<br /><br /> DropDownCombo<br /> VSPackage несет ответственность за заполнение содержимое для этого поля со списком. Пользователь не может вводить ничего в текстовом поле этом раскрывающемся списке.<br /><br /> DynamicCombo<br /> VSPackage несет ответственность за заполнение содержимое этого поля со списком. Пользователь может изменить поля со списком и также выбрать элементы в нем.<br /><br /> IndexCombo<br /> Так же, как DynamicCombo, за исключением того, он вызывает индекс элемента, а не его текст.<br /><br /> MRUCombo<br /> Заполнить по интегрированной среде разработки (IDE) от имени пакета VSPackage.  Пользователь может редактировать в этом поле со списком. Интегрированная среда разработки запоминает до 16 последних записей в поле со списком.<br /><br /> Когда пользователь выбирает что-то в поле со списком или вводит что-то новое, интегрированной среды разработки уведомляет соответствующие VSPackage.|  
|Условие|Необязательный параметр. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|Родительский|Необязательный параметр. Родительский элемент кнопки.|  
|CommandFlag|Обязательный. См. в разделе [элемент commandflag](../extensibility/command-flag-element.md). Ниже приведены допустимые значения CommandFlag для кнопки.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -Фильтрации<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|Строки|Обязательный. См. в разделе [элемент Strings](../extensibility/strings-element.md). Дочерний элемент ButtonText должны быть определены.|  
|Комментарий|Дополнительный комментарий.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Элемент Commands](../extensibility/commands-element.md)|Представляет коллекцию команд на панели инструментов для VSPackage.|  
  
## <a name="example"></a>Пример  
  
```xml  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  priority="0x0500" type="DropDownCombo" defaultWidth="100"  
  idCommandList="cmdidGetInsertOptionsList">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
```  
  
## <a name="see-also"></a>См. также  
 [Visual Studio командные файлы table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
