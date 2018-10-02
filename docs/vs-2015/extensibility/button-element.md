---
title: Кнопки элемент | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad49fd053a10938dcc9f038ff7385bcd93c6253f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558960"
---
# <a name="button-element"></a>Элемент Button
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [элемент Button](https://docs.microsoft.com/visualstudio/extensibility/button-element).  
  
Определяет элемент, который пользователь может взаимодействовать с. Кнопки могут быть разных типов: кнопки, MenuButton и SplitDropDown.  
  
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
|guid|Обязательно. Идентификатор GUID идентификатора GUID и идентификатора команды.|  
|id|Обязательно. Идентификатор GUID и идентификатора идентификатор команды.|  
|priority|Необязательный. Числовое значение, указывающее приоритет.|  
|type|Необязательный. Значение перечисления, которое указывает тип кнопки.<br /><br /> Если не указан, используется кнопка.<br /><br /> Кнопка<br /> Стандартные команды, которая отображается на панели инструментов (обычно виде преобразованного в значок кнопки), меню и контекстные меню.<br /><br /> MenuButton<br /> Пункт меню, который не выполняет команду, но дает другое меню.<br /><br /> SplitDropDown<br /> Элементы управления, например кнопки отмены и повтора на стандартной панели инструментов в Microsoft Word.|  
|Условие|Необязательный. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Parent](../extensibility/parent-element.md)|Необязательный. Родительский элемент кнопки.|  
|[Элемент Icon](../extensibility/icon-element.md)|Необязательный. Значок, связанный с кнопкой.|  
|[Элемент CommandFlag](../extensibility/command-flag-element.md)|Обязательно. Ниже приведены допустимые значения CommandFlag для кнопки.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextChanges<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Элемент Strings](../extensibility/strings-element.md)|Обязательно. Дочерние [элемент ButtonText](../extensibility/buttontext-element.md) должен быть определен.|  
|Комментарий|Дополнительный комментарий.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Buttons](../extensibility/buttons-element.md)|Группирует элементы кнопки.|  
  
## <a name="example"></a>Пример  
 В следующем примере определяется кнопки в vsct-файл.  
   
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

