---
title: Элемент SafeControl | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e6b47254a80c9cdadab6ca18f2fb8c3e8540fbd0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827349"
---
# <a name="safecontrol-element"></a>SafeControl - элемент
  Представляет элемент управления ASPX или веб-части, которое обозначается как безопасные для любого доступа пользователя к любой странице ASPX на сайте SharePoint.

## <a name="syntax"></a>Синтаксис

```xml
<SafeControl Assembly = "Name of assembly that contains the safe control"
    IsSafe = "true/false"
    IsSafeAgainstScript = "true/false"
    Name = "Name of this safe control entry"
    Namespace = "Namespace of the safe control"
    TypeName = "Type of the safe control" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|**Assembly**|Необязательный **xs: String** атрибута.<br /><br /> Имя сборки, в котором определен элемент управления ASPX или веб-части. По умолчанию использует этот атрибут **$SharePoint.Project.AssemblyFullName$** подставляемый в качестве имени сборки. Дополнительные сведения см. в разделе [подстановочных параметров](../sharepoint/replaceable-parameters.md).|
|**IsSafe**|Необязательный **xs: Boolean** атрибута.<br /><br /> Указывает, является безопасная настройка для недоверенных пользователей для доступа к ли элемент управления ASPX или веб-части.|
|**IsSafeAgainstScript**|Необязательный **xs: Boolean** атрибута.<br /><br /> Указывает ли пользователи без доверия можно просмотреть или изменить свойства элемента управления ASPX или веб-части.|
|**Name**|Необязательный **xs: String** атрибута.<br /><br /> Имя этой записи безопасного элемента управления в коллекции.|
|**Пространство имен**|Необязательный **xs: String** атрибута.<br /><br /> Пространство имен элемента управления ASPX или веб-части.|
|**Имя типа**|Необязательный **xs: String** атрибута.<br /><br /> Имя типа элемента управления ASPX или веб-части.|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[SafeControls](../sharepoint/safecontrols-element.md)|Представляет коллекцию элементов управления ASPX и веб-частей, отмеченных как безопасные для любого доступа пользователя к любой странице ASPX на сайте SharePoint.|

## <a name="remarks"></a>Примечания
 Дополнительные сведения о безопасных элементов управления, см. в разделе [сведениями упаковки и развертывания в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Сведения об элементе

|||
|-|-|
|**Пространство имен**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|ProjectItemModelSchema.xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также
- [Справочник по схеме для элемента проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Предоставляют сведения о упаковки и развертывания в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
