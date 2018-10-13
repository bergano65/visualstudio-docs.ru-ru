---
title: Элемент RequiredFrameworkVersion (шаблоны Visual Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 374ee45be29dd51a2a29d1c949939d1d3b939aa3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49171800"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Элемент RequiredFrameworkVersion (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает Минимальная версия .NET Framework, требуемый шаблоном. Иерархия схемы.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<RequiredFrameworkVersion >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет, как он отображается в любом категорию шаблона и **новый проект** или **Добавление нового элемента** диалоговое окно.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Этот текст должен быть минимальный номер версии платформы .NET Framework, которая необходима для шаблона.  
  
## <a name="remarks"></a>Примечания  
 `RequiredFrameworkVersion` — это необязательный элемент. Этот элемент используется в том случае, если шаблон поддерживает только определенную минимальную версию и более поздних версий, если таковое имеется, платформы .NET Framework.  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Настройка конкретной версии платформы .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)

