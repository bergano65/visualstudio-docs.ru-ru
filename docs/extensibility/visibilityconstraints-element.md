---
title: "Элемент VisibilityConstraints | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f26268e6168379632868c07a9d9c58f9485c8ada
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="visibilityconstraints-element"></a>Элемент VisibilityConstraints
Элемент VisibilityConstraints определяет видимость статических групп, команд и панелей инструментов. Видимость управляется сначала [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE) без загрузки VSPackage.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|Условие|Необязательно. В разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент VisibilityItem](../extensibility/visibilityitem-element.md)|Определяет видимость статических команды и панели инструментов.|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Определяет видимость статических групп, команд и панелей инструментов.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, которые представляют команды (например, пункты меню, меню, панелей инструментов и поля со списком), которые VSPackage предоставляет интегрированную среду разработки.|  
  
## <a name="example"></a>Пример  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>См. также  
 [Элемент VisibilityItem](../extensibility/visibilityitem-element.md)   
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)