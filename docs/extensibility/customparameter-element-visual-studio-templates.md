---
title: "Элемент CustomParameter (шаблоны Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords: CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d52d22e3b4200cee0bd5d3dd3eab3e5356f0dbbd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="customparameter-element-visual-studio-templates"></a>Элемент CustomParameter (шаблоны Visual Studio)
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
|`Name`|Обязательный. Имя параметра. Формат для параметров: $*имя*$.|  
|`Value`|Обязательный. Значение замены для параметра.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Группирует пользовательские параметры, которые могут быть переданы в мастер шаблонов, когда мастер замены параметров.|  
  
## <a name="remarks"></a>Примечания  
 Если шаблон содержит `CustomParameter` элементов, каждый экземпляр `Name` атрибут заменяется `Value` атрибута в создаваемых файлов проекта или элемента.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать несколько пользовательских параметров в шаблоне. При создании проекта или элемента из шаблона с помощью следующих пользовательских параметров, все экземпляры `$color1$` и `$color2$` в шаблоне файлы будут заменены `Red` и `Blue`соответственно.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>См. также  
 [Customparameters-элемент (шаблоны Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Параметры шаблона](../ide/template-parameters.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)