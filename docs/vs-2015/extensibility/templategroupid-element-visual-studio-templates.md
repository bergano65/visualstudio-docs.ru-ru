---
title: Элемент TemplateGroupID (шаблоны Visual Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a6c2852938e77f87143b3ddd15fce0a4a6e5bcd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203922"
---
# <a name="templategroupid-element-visual-studio-templates"></a>Элемент TemplateGroupID (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает, в каком типе проекта будут отображаться шаблоны элементов. Этот элемент действителен, когда [ShowByDefault (шаблоны Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) присваивается `false`. При [ShowByDefault (шаблоны Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) присваивается `true`, а затем шаблон элементов доступен во всех типах проектов.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<TemplateGroupID >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Этот текст задает идентификатор для категории шаблонов элементов.  
  
## <a name="remarks"></a>Примечания  
 `TemplateGroupID` является элементом.  
  
 Значение `TemplateGroupID` используется вместе с регистрацией системы проектов (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<номер версии >* \Projects\\) для фильтрации шаблонов, которые отображаются в **Добавление нового элемента** диалоговое окно.  
  
|Значение Visual C++|Значение|  
|------------------------|-------------|  
|VC-Native|Используется для собственных проектов. Кроме того, используется по умолчанию, когда не удается определить тип проекта.|  
|VC-Managed|Используется для управляемых проектов (/clr).|  
|VC-Windows|Используется для всех проектов, нацеленных на платформу Windows (машинный код/управляемый код/хранилище).|  
|WinRT-Native-UAP|Используется для проектов хранилища Windows 10.|  
|CodeSharing-Native|Используется для общих проектов элементов.|  
|WinRT-Native-6.3|Используется для проектов Магазина Windows 8.1.|  
|WinRT-Native-Phone-6.3|Используется для проектов Магазина Windows Phone 8.1.|  
|WinRT-Native|Используется для проектов Магазина Windows 8.0.|  
|VC-Android|Используется для проектов Android.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)

