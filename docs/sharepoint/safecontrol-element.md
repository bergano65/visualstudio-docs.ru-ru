---
title: Элемент SafeControl | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e8cf6d3d168e3d12d74a9773ccfb3312a29046f7
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2018
---
# <a name="safecontrol-element"></a>Элемент SafeControl
  Представляет элемент управления ASPX или веб-части, которые обозначены как безопасные для любому пользователю получить доступ к любой странице ASPX на сайте SharePoint.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|**Assembly**|Необязательный **xs: String** атрибута.<br /><br /> Имя сборки, в которой определен элемент управления ASPX или веб-части. По умолчанию этот атрибут используется **$SharePoint.Project.AssemblyFullName$** заменяемый параметр для имени сборки. Дополнительные сведения см. в разделе [подстановочные параметры](../sharepoint/replaceable-parameters.md).|  
|**IsSafe**|Необязательный **xs: Boolean** атрибута.<br /><br /> Указывает, является ли элемент управления ASPX или веб-часть безопасная настройка для недоверенных пользователей для доступа к.|  
|**IsSafeAgainstScript**|Необязательный **xs: Boolean** атрибута.<br /><br /> Указывает, можно ли ненадежные пользователи просмотреть или изменить свойства элемента управления ASPX или веб-части.|  
|**Name**|Необязательный **xs: String** атрибута.<br /><br /> Имя этой записи безопасных элементов управления в коллекции.|  
|**Пространство имен**|Необязательный **xs: String** атрибута.<br /><br /> Пространство имен элемента управления ASPX или веб-части.|  
|**Имя типа**|Необязательный **xs: String** атрибута.<br /><br /> Имя типа элемента управления ASPX или веб-части.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Представляет коллекцию элементов управления ASPX и веб-частей, отмеченных как безопасные для любому пользователю получить доступ к любой странице ASPX на сайте SharePoint.|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о безопасных элементов управления см. в разделе [предоставление упаковке и сведения о развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым.**|Нет|  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме элементов проектов SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  