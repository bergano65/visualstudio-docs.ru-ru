---
title: Requiredplatformversion-элемент (шаблоны Visual Studio) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35a8dc6fa57dbe88ce1e30e9be58105f28fe5641
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion - элемент (шаблоны Visual Studio)
Указывает минимальную версию операционной системы, шаблона проекта требуется для правильной работы. Этот элемент используется для шаблонов проектов, которые создают [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] приложений.  
  
 `RequiredPlatformVersion` Значение сравнивается непосредственно с версией операционной системы. Если `RequiredPlatformVersion` выше, чем версия операционной системы, шаблон не отображается в **новый проект** диалоговое окно. Для указания шаблона для [!INCLUDE[win8](../debugger/includes/win8_md.md)] или более поздней версии, задайте `RequiredPlatformVersion` для 6.2.0. Для указания шаблона для [!INCLUDE[win81](../debugger/includes/win81_md.md)] или более поздней версии, необходимо задать RequiredPlatformVersion для 6.3.0.  
  
 Шаблоны, которые указывают `RequiredPlatformVersion`= 8, совместимы с предыдущей клиента [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] шаблонов.  
  
 VSTemplate  
TemplateData  
..... TargetPlatformName  
RequiredPlatformVersion  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 Отсутствует.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Задает платформу, для которой предназначен шаблон проекта.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
## <a name="remarks"></a>Примечания  
 Данный текст задает минимальную версию операционной системы требуемую для шаблона.  
  
## <a name="example"></a>Пример  
 В этом примере указывается, что шаблон проекта предназначен для [!INCLUDE[win8](../debugger/includes/win8_md.md)] или более поздней версии.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>См. также  
 [TargetPlatformName-элемент (шаблоны Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)