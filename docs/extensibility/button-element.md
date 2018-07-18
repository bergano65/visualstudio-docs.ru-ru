---
title: Кнопку элемент | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 78b5abd8762669db4e225a68817f2c9823a49267
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109634"
---
# <a name="button-element"></a>Элемент Button
Определяет элемент, который пользователь может взаимодействовать с. Кнопки могут быть разных типов: кнопка, MenuButton и SplitDropDown.  
  
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
|guid|Обязательно. Идентификатор GUID идентификатор GUID или идентификатор команды.|  
|id|Обязательно. Идентификатор идентификатор GUID или идентификатор команды.|  
|priority|Необязательный. Числовое значение, указывающее приоритет.|  
|type|Необязательный. Перечисляемое значение, указывающее тип кнопки.<br /><br /> Если не указан, используется кнопка.<br /><br /> Кнопка<br /> Стандартная команда, которая отображается на панели инструментов (обычно виде кнопки, преобразованного в значок), меню и контекстные меню.<br /><br /> MenuButton<br /> Пункт меню, который не выполняет команду, но дает другое меню.<br /><br /> SplitDropDown<br /> Элементы управления, такие как кнопки отмены и повтора на стандартной панели инструментов в Microsoft Word.|  
|Условие|Необязательный. В разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Parent](../extensibility/parent-element.md)|Необязательный. Родительский элемент кнопки.|  
|[Элемент Icon](../extensibility/icon-element.md)|Необязательный. Значок, связанный с кнопкой.|  
|[Элемент CommandFlag](../extensibility/command-flag-element.md)|Обязательно. Ниже приведены допустимые значения CommandFlag для кнопки.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextChanges<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Элемент Strings](../extensibility/strings-element.md)|Обязательно. Дочерние [элемент ButtonText](../extensibility/buttontext-element.md) должен быть определен.|  
|Комментарий|Необязательный комментарий.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Buttons](../extensibility/buttons-element.md)|Группирует элементы кнопки.|  
  
## <a name="example"></a>Пример  
 В следующем примере определяется кнопки в vsct-файле.  

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```
 
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)