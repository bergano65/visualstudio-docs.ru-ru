---
title: Элемент CommandPlacement | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 43fd417c4d54c0ab57133cf6dbff2c770c1ffc45
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979511"
---
# <a name="commandplacement-element"></a>Элемент CommandPlacement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Элемент CommandPlacement включает кнопки, группы и меню, должны быть включены в более чем одной группе или меню. С помощью элемента CommandPlacement, у вас нет полностью переопределить эти элементы, чтобы изменить внешний вид пользовательского интерфейса.  
  
 Дополнительные сведения см. в разделе [группы кнопок для повторного использования создание](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательный. Идентификатор guid набора команд, как определено в [элемент Symbols](../extensibility/symbols-element.md).|  
|id|Обязательный. Идентификатор меню, группу или команду, чтобы поместить, как определено в `Symbols Element`.|  
|priority|Обязательный. Определяет визуальную позицию элемента в его родительском элементе.|  
|Условие|Необязательный параметр. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
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
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
