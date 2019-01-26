---
title: Элемент CommandPlacement | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 016c1f88cff82e0bbe824bf3364c9123384a7470
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021303"
---
# <a name="commandplacement-element"></a>Элемент CommandPlacement
Элемент CommandPlacement включает кнопки, группы и меню, должны быть включены в более чем одной группе или меню. С помощью элемента CommandPlacement, у вас нет полностью переопределить эти элементы, чтобы изменить внешний вид пользовательского интерфейса.  
  
 Дополнительные сведения см. в разделе [создание повторно используемых групп кнопок](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательный. Идентификатор guid набора команд, как определено в [элемент Symbols](../extensibility/symbols-element.md).|  
|id|Обязательный. Идентификатор меню, группу или команду, чтобы поместить, как определено в `Symbols Element`.|  
|priority|Обязательный. Определяет визуальную позицию элемента в его родительском элементе.|  
|Условие|Необязательный параметр. См. в разделе [условного Aattributes](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|Родительский|Обязательный. Меню или группы, на котором размещается элемент, чтобы разместить.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент CommandPlacements](../extensibility/commandplacements-element.md)|Указывает группы элементов CommandPlacements и CommandPlacement.|  
  
## <a name="example"></a>Пример  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>См. также  
 [Элемент CommandPlacements](../extensibility/commandplacements-element.md)   
 [Visual Studio командные файлы table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
