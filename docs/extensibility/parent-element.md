---
title: Родительский элемент | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbfb014e57f793bb39d696ac311c4f27884500f4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949728"
---
# <a name="parent-element"></a>Родительский элемент
Группу можно только родительский кнопку или поле со списком. Родительского меню или группы, возможно, другие меню или группу. В [элемент CommandPlacement](../extensibility/commandplacement-element.md), этот элемент является обязательным; во всех остальных случаях это необязательно. Если этот элемент указан, предком `Group_Undefined:0` будет содержится в разрешении.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|guid|Обязательный. Идентификатор GUID из идентификатора GUID и идентификатора команды.|  
|id|Обязательный. Идентификатор команды идентификатор из GUID и идентификатора.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Нет  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, которые представляют команды, предоставляемых VSPackage интегрированной среды разработки (IDE). Например пункты меню, меню, панелей инструментов и поля со списком.|  
|[Элемент Buttons](../extensibility/buttons-element.md)|Группы [элемент Button](../extensibility/button-element.md) элементов.|  
|[Элемент меню](../extensibility/menus-element.md)|Определяет все меню, которые реализует VSPackage.|  
|[Элемент Groups](../extensibility/groups-element.md)|Содержит записи, которые определяют группы команд пакета VSPackage.|  
  
## <a name="see-also"></a>См. также  
 [Visual Studio командные файлы table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)