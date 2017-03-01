---
title: "Элемент TemplateID (шаблоны Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a69f3c22a6984c0ce18052e18dcf0ba4603d0c31
ms.lasthandoff: 02/22/2017

---
# <a name="templateid-element-visual-studio-templates"></a>Элемент TemplateID (шаблоны Visual Studio)
Указывает идентификатор для шаблона элемента, который относится к категории группы шаблонов элементов, [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) элемента.  
  
 \<VSTemplate настроек  
 \<TemplateData настроек  
 \<Идентификатор шаблона настроек  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<TemplateID> ... </TemplateID>  
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
 Объект `string` , представляющий идентификатор шаблона элемента, который относится к категории группы шаблонов элементов, `TemplateGroupID` элемент.  
  
## <a name="remarks"></a>Примечания  
 `TemplateID` — это необязательный элемент.  
  
 Если опущены VSTEMPLATE-файл `TemplateID` элемент, а затем [имя](../extensibility/name-element-visual-studio-templates.md) элемент используется как идентификатор для шаблона.  
  
 Значение `TemplateID` элемента используется вместе с регистрации системы проекта (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\) с шаблонами фильтра, которые отображаются в **Добавление нового элемента** диалоговое окно.  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
