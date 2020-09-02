---
title: Элемент Рекуиредплатформверсион (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e5ba8cfef6674b5603cf03c73619f686338af3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159287"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion - элемент (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает минимальную версию операционной системы, которую должен правильно работать шаблон проекта. Этот элемент используется для шаблонов проектов, которые создают [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] приложения.  
  
 `RequiredPlatformVersion`Значение сравнивается непосредственно с версией операционной системы. Если значение `RequiredPlatformVersion` выше версии операционной системы, шаблон не отображается в диалоговом окне **Новый проект** . Чтобы указать шаблон для [!INCLUDE[win8](../includes/win8-md.md)] или более поздней версии, задайте для параметра значение `RequiredPlatformVersion` 6.2.0. Чтобы указать шаблон для [!INCLUDE[win81](../includes/win81-md.md)] или более поздней версии, установите для параметра рекуиредплатформверсион значение 6.3.0.  
  
 Шаблоны, которые указывают `RequiredPlatformVersion` = 8, совместимы с предыдущими [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] шаблонами клиента.  
  
 VSTemplate  
TemplateData  
..... таржетплатформнаме  
RequiredPlatformVersion  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 Нет.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[темплатеплатформнаме](../extensibility/templatedata-element-visual-studio-templates.md)|Задает платформу, для которой предназначен шаблон проекта.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
## <a name="remarks"></a>Remarks  
 Этот текст указывает минимальную версию операционной системы, требуемую для шаблона.  
  
## <a name="example"></a>Пример  
 В этом примере указывается, что шаблон проекта предназначен для [!INCLUDE[win8](../includes/win8-md.md)] или более поздней версии.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Элемент Таржетплатформнаме (шаблоны Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
