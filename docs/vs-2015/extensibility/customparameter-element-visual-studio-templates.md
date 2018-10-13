---
title: Элемент CustomParameter (шаблоны Visual Studio) | Документация Майкрософт
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
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9540b42497b15eace2ed7a54ef9c26f76c0576a6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49198852"
---
# <a name="customparameter-element-visual-studio-templates"></a>Элемент CustomParameter (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Содержит имя пользовательского параметра и значение, используемое при создании проекта или элемента из шаблона.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Name`|Обязательно. Имя параметра. Формат для параметров: $*имя*$.|  
|`Value`|Обязательно. Значение замены для параметра.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Группирует пользовательские параметры, которые должны быть переданы мастера шаблонов, когда мастер замены параметров.|  
  
## <a name="remarks"></a>Примечания  
 Если шаблон содержит `CustomParameter` элементов, каждый экземпляр `Name` атрибут заменяется `Value` атрибут в создаваемых файлов проекта или элемента.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать несколько пользовательских параметров в шаблоне. При создании проекта или элемента из шаблона, выполнив следующие пользовательские параметры, все экземпляры `$color1$` и `$color2$` в шаблоне файлов будет заменен `Red` и `Blue`, соответственно.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>См. также  
 [Элемент CustomParameters (шаблоны Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Параметры шаблона](../ide/template-parameters.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)

