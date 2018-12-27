---
title: Элемент TemplateID (шаблоны Visual Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eda4b3134d8e7e589c60ee8b8860042b7e0f1ff5
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53560548"
---
# <a name="templateid-element-visual-studio-templates"></a>Элемент TemplateID (шаблоны Visual Studio)
Задает идентификатор шаблона элемента, который относится к категории группы шаблонов элементов по [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) элемент.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<TemplateID >  
  
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
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|  
  
## <a name="text-value"></a>Текстовое значение  
 Объект `string` , представляющий идентификатор шаблона элемента, который относится к категории группы шаблонов элементов по `TemplateGroupID` элемент.  
  
## <a name="remarks"></a>Примечания  
 `TemplateID` — это необязательный элемент.  
  
 Если файл .vstemplate не содержит `TemplateID` элемент, а затем [имя](../extensibility/name-element-visual-studio-templates.md) элемент используется в качестве идентификатора для шаблона.  
  
 Значение `TemplateID` используется вместе с регистрацией системы проектов (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\) для фильтрации шаблонов, которые отображаются в **Добавление нового элемента** диалоговое окно.  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)