---
title: Элемент SortOrder (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 825ec785a83cae0aaa8a31ae1375e956228b634e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205517"
---
# <a name="sortorder-element-visual-studio-templates"></a>Элемент SortOrder (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Задает значение, используемое для упорядочения шаблона (помимо других шаблонов в той же категории), которое отображается в диалоговом окне **Создание проекта** или **Добавление нового элемента** .  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<SortOrder>  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<SortOrder> ... </SortOrder>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Объект `integer` , представляющий значение порядка сортировки.  
  
## <a name="remarks"></a>Remarks  
 Параметр `SortOrder` является необязательным элементом. Значение по умолчанию — 100, а все значения должны быть кратными 10.  
  
 `SortOrder`Элемент не учитывается для шаблонов, созданных пользователем. Все созданные пользователем шаблоны сортируются в алфавитном порядке.  
  
 Шаблоны с низким порядком сортировки отображаются в диалоговом окне **Создание проекта** или **Добавление элемента** перед шаблонами, имеющими значения с высоким порядком сортировки.  
  
## <a name="example"></a>Пример  
 В следующем примере показаны метаданные для стандартного [!INCLUDE[csprcs](../includes/csprcs-md.md)] шаблона класса.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 В этом примере `SortOrder` элемент относительно высокий. Вполне вероятно, что другие [!INCLUDE[csprcs](../includes/csprcs-md.md)] шаблоны элементов будут иметь `SortOrder` значение ниже `290` и будут отображаться перед этим шаблоном в диалоговом окне **новый элемент** .  
  
## <a name="see-also"></a>См. также:  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
