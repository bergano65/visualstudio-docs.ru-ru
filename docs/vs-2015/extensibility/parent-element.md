---
title: Родительский элемент | Документация Майкрософт
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
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b16aa3e3d6542130b449196de92e795e464ab0e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563321"
---
# <a name="parent-element"></a>Элемент Parent
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [родительского элемента](https://docs.microsoft.com/visualstudio/extensibility/parent-element).  
  
Группу можно только родительский кнопку или поле со списком. Родительского меню или группы, возможно, другие меню или группу. В [элемент CommandPlacement](../extensibility/commandplacement-element.md), этот элемент является обязательным; во всех остальных случаях это необязательно. Если этот элемент указан, предком `Group_Undefined:0` будет содержится в разрешении.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательно. Идентификатор GUID из идентификатора GUID и идентификатора команды.|  
|id|Обязательно. Идентификатор команды идентификатор из GUID и идентификатора.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Нет  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, которые представляют команды, предоставляемых VSPackage интегрированной среды разработки (IDE). Например пункты меню, меню, панелей инструментов и поля со списком.|  
|[Элемент Buttons](../extensibility/buttons-element.md)|Группы [элемент Button](../extensibility/button-element.md) элементов.|  
|[Элемент Menus](../extensibility/menus-element.md)|Определяет все меню, которые реализует VSPackage.|  
|[Элемент Groups](../extensibility/groups-element.md)|Содержит записи, которые определяют группы команд пакета VSPackage.|  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

