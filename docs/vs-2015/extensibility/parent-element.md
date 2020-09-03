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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194080"
---
# <a name="parent-element"></a>Родительский элемент
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Родительским элементом кнопки или поля со списком может быть только группа. Родительским элементом меню или группы может быть любое другое меню или группа. В [элементе CommandPlacement](../extensibility/commandplacement-element.md)этот элемент является обязательным; во всех остальных случаях это необязательно. Если этот элемент опущен, то родительский объект `Group_Undefined:0` будет подразумеваемым.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательный. Идентификатор GUID идентификатора команды GUID/ID.|  
|идентификатор|Обязательный. Идентификатор идентификатора команды GUID/ID.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Нет  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды, предоставляемые пакетом VSPackage в интегрированной среде разработки (IDE). Например, пункты меню, меню, панели инструментов и поля со списком.|  
|[Элемент Buttons](../extensibility/buttons-element.md)|Группирует элементы [элемента Button](../extensibility/button-element.md) .|  
|[Элемент Menus](../extensibility/menus-element.md)|Определяет все меню, которые реализует VSPackage.|  
|[Groups, элемент](../extensibility/groups-element.md)|Содержит записи, определяющие группы команд VSPackage.|  
  
## <a name="see-also"></a>См. также:  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
