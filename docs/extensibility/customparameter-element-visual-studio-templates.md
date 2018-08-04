---
title: Элемент CustomParameter (шаблоны Visual Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: de6f5bf513d9d3582ba05bf7a34471d13743f8de
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500687"
---
# <a name="customparameter-element-visual-studio-templates"></a>Элемент CustomParameter (шаблоны Visual Studio)
Содержит имя пользовательского параметра и значение, используемое при создании проекта или элемента из шаблона.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Name`|Обязательно. Имя параметра. Формат для параметров: $*имя*$.|  
|`Value`|Обязательно. Значение замены для параметра.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
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