---
title: "Родительский элемент | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 0da0bd0aceaccdbf8d2cf11fd3490a3e5810ad2e
ms.lasthandoff: 02/22/2017

---
# <a name="parent-element"></a>Элемент Parent
Родительские поля кнопку или поле со списком может быть только группу. Родительского меню или группы может быть любым другим меню или группы. В [CommandPlacement элемент](../extensibility/commandplacement-element.md), этот элемент является обязательным; во всех остальных случаях это необязательно. Если этот элемент указан, родительский `Group_Undefined:0` будет неявно.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательный. Идентификатор GUID из идентификатора GUID и идентификатор команды.|  
|id|Обязательный. Идентификатор команды, идентификатор из GUID-идентификатор.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Нет  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды, которые VSPackage предоставляет интегрированную среду разработки (IDE). Например элементы меню, меню, панелей инструментов и поля со списком.|  
|[Элемент кнопки](../extensibility/buttons-element.md)|Группы [элемент Button](../extensibility/button-element.md) элементы.|  
|[Элемент меню](../extensibility/menus-element.md)|Определяет все меню, которые реализует VSPackage.|  
|[Элемент Groups](../extensibility/groups-element.md)|Содержит элементы, которые определяют группы команды VSPackage.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы команд Visual Studio (. Файлы Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
