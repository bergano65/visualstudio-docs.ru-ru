---
title: "Элемент поля со списком | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Элемент комбинировать (VSCT XML-схемы)"
  - "Элементы схемы VSCT XML, комбинировать"
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Элемент поля со списком
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет команды, которые отображаются в поле со списком. Существует четыре вида поля со списком, следующим образом: DropDownCombo, DynamicCombo, IndexCombo и MRUCombo.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательный. Идентификатор GUID идентификатор GUID и идентификатор команды.|  
|id|Обязательный. Идентификатор идентификатор GUID и идентификатор команды.|  
|defaultWidth|Обязательный. Целое число, указывающее ширину точек для поля со списком.|  
|idCommandList|Обязательный. Идентификатор, который отправляется целевой active команда для получения списка элементов, которые отображаются в поле со списком. Идентификатор будет в той же области GUID, что и элемент управления.|  
|priority|Необязательно. Числовое значение, указывающее приоритет.|  
|тип|Необязательно. Значение перечисления, указывающее тип кнопки.<br /><br /> Если не указан, используется кнопка.<br /><br /> DropDownCombo<br /> VSPackage отвечает за заполнение содержимое этого поля со списком. Пользователь не может ввести ничего в этом раскрывающемся списке в текстовое поле.<br /><br /> DynamicCombo<br /> Для заполнения содержимого списком отвечает VSPackage. Пользователь может изменить поля со списком и также выбрать элементы в.<br /><br /> IndexCombo<br /> Таким же, как DynamicCombo, за исключением того, что он создает индекс элемента, а не его текст.<br /><br /> MRUCombo<br /> Заполненных интегрированную среду разработки (IDE) от имени VSPackage.  Пользователь может редактировать в этом поле со списком. Интегрированная среда Разработки запоминает до 16 последних записей в поле со списком.<br /><br /> Когда пользователь выбирает что-либо в поле со списком или вводит новое значение, интегрированной среды Разработки уведомляет соответствующие VSPackage.|  
|Условие|Необязательно. В разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Родительский|Необязательно. Родительский элемент кнопки.|  
|CommandFlag|Обязательный. В разделе [команды элемент флаг](../extensibility/command-flag-element.md). Ниже приведены допустимые значения CommandFlag для кнопки.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -Фильтрация<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|Строки|Обязательный. В разделе [строки элемента](../extensibility/strings-element.md). Должен быть определен ButtonText дочернего элемента.|  
|Комментарий|Необязательный комментарий.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Commands](../extensibility/commands-element.md)|Представляет коллекцию команд на панели инструментов VSPackage.|  
  
## <a name="example"></a>Пример  
  
```  
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
 [Таблицы команд Visual Studio (. Файлы Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)