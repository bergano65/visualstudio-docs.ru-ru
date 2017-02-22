---
title: "Элемент Button | Microsoft Docs"
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
  - "Элемент кнопки (VSCT XML-схемы)"
  - "Элементы схемы VSCT XML, кнопки"
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Элемент Button
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет элемент, который пользователь может взаимодействовать с. Кнопки могут быть различных типов: кнопка, MenuButton и SplitDropDown.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательный. Идентификатор GUID идентификатор GUID и идентификатор команды.|  
|id|Обязательный. Идентификатор идентификатор GUID и идентификатор команды.|  
|priority|Необязательно. Числовое значение, указывающее приоритет.|  
|тип|Необязательно. Значение перечисления, указывающее тип кнопки.<br /><br /> Если не указан, используется кнопка.<br /><br /> Кнопка<br /> Стандартная команда меню и контекстные меню (обычно в виде пиктограммы кнопки), отображается на панели инструментов.<br /><br /> MenuButton<br /> Элемент меню, выполнение команды, но выдает другой меню.<br /><br /> SplitDropDown<br /> Элементы управления, например кнопки отмены и повтора на стандартной панели инструментов в Microsoft Word.|  
|Условие|Необязательно. В разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Родительский элемент](../extensibility/parent-element.md)|Необязательно. Родительский элемент кнопки.|  
|[Значок элемента](../extensibility/icon-element.md)|Необязательно. Значок, связанный с кнопкой.|  
|[Элемент Command флаг](../extensibility/command-flag-element.md)|Обязательный. Ниже приведены допустимые значения CommandFlag для кнопки.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextChanges<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Элемент строки](../extensibility/strings-element.md)|Обязательный. Дочерние [ButtonText элемента](../extensibility/buttontext-element.md) должен быть определен.|  
|Комментарий|Необязательный комментарий.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент кнопки](../extensibility/buttons-element.md)|Группирует элементы кнопки.|  
  
## <a name="example"></a>Пример  
 В следующем примере определяется кнопки в файл .vsct.  
  
 [!CODE [MenuText#02](../CodeSnippet/VS_Snippets_VSSDK/menutext#02)]  
  
## <a name="see-also"></a>См. также  
 [Таблицы команд Visual Studio (. Файлы Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)