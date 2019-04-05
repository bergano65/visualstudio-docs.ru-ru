---
title: Родительский элемент | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2086473bc484fed4e8e351f0c3838074557586c9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980212"
---
# <a name="parent-element"></a>Элемент Parent
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
|guid|Обязательный. Идентификатор GUID из идентификатора GUID и идентификатора команды.|  
|id|Обязательный. Идентификатор команды идентификатор из GUID и идентификатора.|  
  
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
