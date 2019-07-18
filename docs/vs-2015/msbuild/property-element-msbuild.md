---
title: Элемент Property (MSBuild) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eefe0160328f1eb6b3fe841742547efe8be50ec1
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664834"
---
# <a name="property-element-msbuild"></a>Элемент Property (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Содержит определяемое пользователем имя свойства и значение. Каждое свойство, используемое в проекте [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], должно быть указано в качестве дочернего для элемента `PropertyGroup`.  
  
 \<Project>  
 \<PropertyGroup>  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Property Condition="'String A' == 'String B'">  
    Property Value  
</Property>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Группирующий элемент для свойств.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является необязательным.  
  
 Этот текст указывает значение свойства и может содержать XML.  
  
## <a name="remarks"></a>Примечания  
 Имена свойств ограничены только символами ASCII. Значения свойств указываются в проекте путем размещения имени свойства между "`$(`" и "`)`". Например, `$(builddir)\classes` разрешится в "build\classes", если свойство `builddir` будет иметь значение `build`. Дополнительные сведения о свойствах см. в статье [MSBuild Properties](msbuild-properties1.md) (Свойства MSBuild).  
  
## <a name="example"></a>Пример  
 В следующем коде свойству `Optimization` задается значение `false`, а свойству `DefaultVersion` — значение `1.0`, если свойство `Version` является пустым.  
  
```  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>См. также раздел
[Свойства MSBuild](msbuild-properties1.md)  
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
