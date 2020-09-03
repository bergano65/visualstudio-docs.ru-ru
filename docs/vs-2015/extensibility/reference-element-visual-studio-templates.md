---
title: Элемент Reference (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3d67fd19122e160159a6f636516dbca582fe31d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193833"
---
# <a name="reference-element-visual-studio-templates"></a>Элемент Reference (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает ссылку на сборку, которую нужно добавить при добавлении элемента в проект.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<References>  
 \<Reference>  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Reference>  
    <Assembly> ... </Assembly>  
</Reference>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Сборок](../extensibility/assembly-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Указывает сведения о сборке, которую шаблон использует для добавления ссылки на эту сборку в проекты. Каждый элемент должен содержать `Assembly` по одному элементу `Reference` .|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Справочные материалы](../extensibility/references-element-visual-studio-templates.md)|Группирует ссылки на сборки, которые шаблон добавляет в проекты.|  
  
## <a name="remarks"></a>Remarks  
 `Reference` — обязательный дочерний элемент элемента `References`.  
  
 `Reference`Элементы и `References` можно использовать только в VSTEMPLATE-файлах, имеющих `Type` значение атрибута `Item` .  
  
## <a name="example"></a>Пример  
 В следующем примере показан `TemplateContent` элемент шаблона элемента. Этот XML-файл добавляет ссылки на сборки System.dll и System.Data.dll.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
