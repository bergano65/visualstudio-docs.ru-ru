---
title: Элемент SafeControl | Документация Майкрософт
description: Получите сведения об элементе SafeControl, который представляет элемент управления ASPX или веб-часть, помеченную как безопасная для доступа пользователя к странице ASPX сайта SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f08046666ff00d4a0e5489bc78c0c70967774f08
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889477"
---
# <a name="safecontrol-element"></a>SafeControl - элемент
  Представляет элемент управления ASPX или веб-часть, которая обозначена как безопасная для доступа любого пользователя к любой странице ASPX на сайте SharePoint.

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
|**Сборка**|Необязательный атрибут **xs: String** .<br /><br /> Имя сборки, в которой определен элемент управления ASPX или веб-часть. По умолчанию этот атрибут использует заменяемый параметр **$SharePoint. Project. AssemblyFullName $** для имени сборки. Дополнительные сведения см. в разделе [Заменяемые параметры](../sharepoint/replaceable-parameters.md).|
|**Сейф**|Необязательный атрибут **xs: Boolean** .<br /><br /> Указывает, является ли элемент управления ASPX или веб-часть безопасными для доступа недоверенных пользователей.|
|**иссафеагаинстскрипт**|Необязательный атрибут **xs: Boolean** .<br /><br /> Указывает, могут ли недоверенные пользователи просматривать или изменять свойства элемента управления или веб-части ASPX.|
|**Имя**|Необязательный атрибут **xs: String** .<br /><br /> Имя этой записи безопасного элемента управления в коллекции.|
|**Пространство имен**|Необязательный атрибут **xs: String** .<br /><br /> Пространство имен элемента управления ASPX или веб-части.|
|**Имени**|Необязательный атрибут **xs: String** .<br /><br /> Имя типа элемента управления или веб-части ASPX.|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[SafeControls](../sharepoint/safecontrols-element.md)|Представляет коллекцию элементов управления ASPX и веб-части, которые обозначены как безопасные для доступа любого пользователя к любой странице ASPX на сайте SharePoint.|

## <a name="remarks"></a>Remarks
 Дополнительные сведения о безнадежных элементах управления см. [в разделе Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Сведения об элементе

|Свойство|Значение|
|-|-|
|**Пространство имен**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/Шарепоинттулс/Шарепоинтпрожектитеммодел|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|Прожектитеммоделсчема. xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также раздел
- [Справочник по схеме элементов проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
