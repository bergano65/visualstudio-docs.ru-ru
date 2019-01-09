---
title: Элемент ProjectExtensions (MSBuild) | Документы Майкрософт
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc5dd1b98c4cf63aabd1ea48fca8bb5ebbb370b1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828125"
---
# <a name="projectextensions-element-msbuild"></a>Элемент ProjectExtensions (MSBuild)
Позволяет хранить в файлах проектов [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] информацию, не относящуюся к [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Все, что находится внутри элемента `ProjectExtensions`, будет игнорироваться [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  

 \<Project>  
 \<ProjectExtensions>  

## <a name="syntax"></a>Синтаксис  

```xml  
<ProjectExtensions>  
    Non-MSBuild information to include in file.  
</ProjectExtensions>  
```  

## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  

### <a name="attributes"></a>Атрибуты  
 Нет  

### <a name="child-elements"></a>Дочерние элементы  
 Нет  

### <a name="parent-elements"></a>Родительские элементы  

| Элемент | Описание |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Обязательный корневой элемент файла проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] . |

## <a name="remarks"></a>Примечания  
 Только один элемент `ProjectExtensions` может использоваться в проекте [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  

## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется хранение информации из интегрированной среды разработки в элементе `ProjectExtensions`.  

```xml  
<ProjectExtensions>  
    <VSIDE>  
        <External>  
            <!--  
            Raw XML passed to the IDE by an external source  
            -->  
        </External>  
    </VSIDE>  
</ProjectExtensions>  
```  

## <a name="see-also"></a>См. также  
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
