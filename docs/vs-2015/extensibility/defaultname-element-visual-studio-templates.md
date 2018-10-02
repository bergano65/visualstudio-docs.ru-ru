---
title: Элемент DefaultName (шаблоны Visual Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 967bc0a21d9cf860baaff9fa9185c4f4bd81f463
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558662"
---
# <a name="defaultname-element-visual-studio-templates"></a>Элемент DefaultName (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [элемент DefaultName (шаблоны Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/defaultname-element-visual-studio-templates).  
  
Задает имя, система проектов Visual Studio создаст для проекта или элемента при его создании.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<DefaultName >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<DefaultName>  
    Default Project Name  
</DefaultName>  
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
  
 Данный текст задает по умолчанию имя проекта или элемента.  
  
## <a name="remarks"></a>Примечания  
 `DefaultName` — это необязательный элемент.  
  
 Для проектов этот элемент указывает имя каталога, в котором хранится проект на диске. Для элементов он задает имя файла исходного файла.  
  
 При создании проекта или элемента, можно изменить имя по умолчанию, используя **имя** параметр, который доступен из любого **новый проект** диалоговое окно или **Добавление нового элемента** диалоговое окно.  
  
 Если вы не хотите, чтобы система проектов для создания имени по умолчанию для проекта или элемента, затем установите [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) элемент `False`.  
  
## <a name="example"></a>Пример  
 В следующем примере показано метаданные для стандартного шаблона элемента для [!INCLUDE[csprcs](../includes/csprcs-md.md)] класса.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)

