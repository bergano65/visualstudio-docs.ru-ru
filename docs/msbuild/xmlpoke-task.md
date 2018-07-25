---
title: Задача XmlPoke | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d38510799984e1ea690c9c145b7d7664b338f5e
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231266"
---
# <a name="xmlpoke-task"></a>XmlPoke - задача

Задает в XML-файле значения, указанные в запросе XPath.

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `XmlPoke` .
  
|Параметр|Описание:|
|---------------|-----------------|
|`Namespaces`|Необязательный параметр `String` .<br /><br /> Задает пространства имен для префиксов запроса XPath. `Namespaces` — это фрагмент кода XML, состоящий из элементов `Namespace` с атрибутами `Prefix` и `Uri`. Атрибут `Prefix` указывает префикс для привязки к пространству имен, указанному в атрибуте `Uri`. Не используйте пустой `Prefix`.|
|`Query`|Необязательный параметр `String` .<br /><br /> Указывает запрос XPath.|
|`Value`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Задает значение, вставляемое в указанный путь.|
|`XmlInputPath`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает входные данные XML в виде пути к файлу.|

## <a name="remarks"></a>Примечания

 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Пример

Ниже приведен файл sample.xml для изменения:

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

В этом примере, если вы хотите изменить `/Package/mp:PhoneIdentity/PhonePublisherId`, используйте

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Namespace>
        <Namespace Prefix="dn" Uri="http://schemas.microsoft.com/appx/manifest/foundation/windows10" />
        <Namespace Prefix="mp" Uri="http://schemas.microsoft.com/appx/2014/phone/manifest" />
        <Namespace Prefix="uap" Uri="http://schemas.microsoft.com/appx/manifest/uap/windows10" />
    </Namespace>
</PropertyGroup>

<Target Name="Poke">
  <XmlPoke
    XmlInputPath="Sample.xml"
    Value="MyId"
    Query="/dn:Package/mp:PhoneIdentity/@PhoneProductId"
    Namespaces="$(Namespace)"/>
</Target>
</Project>
```

`dn` используется здесь в качестве искусственного префикса пространства имен для пространства имен по умолчанию.

## <a name="see-also"></a>См. также

 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
