---
title: Задача SignFile | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 496017f386e731e553bfce237bd1d2eabea46f49
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976456"
---
# <a name="signfile-task"></a>SignFile - задача

Подписывает указанный файл с помощью заданного сертификата.

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `SignFile` .

 Обратите внимание, что сертификаты SHA-256 разрешены только на компьютерах с .NET 4.5 или более поздней версией.

> [!WARNING]
> Начиная с Visual Studio 2013 с обновлением 3, для этой задачи используется новая подпись, которая позволяет указывать версию целевой платформы для файла. Новую подпись рекомендуется использовать там, где это возможно, поскольку процесс MSBuild работает с хэшами SHA-256 только в том случае, если поддерживается целевая платформа .NET 4.5 или более поздней версии. Если версия целевой платформы .NET 4.0 или ниже, хэш SHA-256 использоваться не будет.

|Параметр|Описание|
|---------------|-----------------|
|`CertificateThumbprint`|Обязательный параметр `String` .<br /><br /> Задает сертификат, который будет использоваться для подписи. Этот сертификат должен находиться в личном хранилище текущего пользователя.|
|`SigningTarget`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Задает файлы, который будут подписаны с помощью сертификата.|
|`TimestampUrl`|Необязательный параметр `String` .<br /><br /> Задает URL-адрес сервера отметок времени.|
|`TargetFrameworkVersion`|Версия платформы .NET Framework, используемой для целевого объекта.|

## <a name="remarks"></a>Примечания

 Помимо перечисленных выше параметров эта задача наследует параметры от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описание см. в статье [Базовый класс Task](../msbuild/task-base-class.md).

## <a name="example"></a>Пример

 В следующем примере используется задача `SignFile` для подписания файлов, указанных в коллекции элементов `FilesToSign`, с помощью сертификата, заданного свойством `Certificate`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <FileToSign Include="File.exe" />
    </ItemGroup>
    <PropertyGroup>
        <Certificate>Cert.cer</Certificate>
    </PropertyGroup>
    <Target Name="Sign">
        <SignFile
            CertificateThumbprint="$(CertificateThumbprint)"
            SigningTarget="@(FileToSign)"
            TargetFrameworkVersion="v4.5" />
    </Target>
</Project>
```

> [!NOTE]
> Отпечатком сертификата является хэш SHA-1 сертификата. Дополнительные сведения см. в статье о [получении хэша SHA-1 сертификата доверенного корневого ЦС](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\)). Если вы копируете и вставляете отпечаток из сведений о сертификате, убедитесь в отсутствии лишнего невидимого знака (3F), из-за которого `SignFile` не сможет обнаружить сертификат.

## <a name="see-also"></a>См. также
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Задачи](../msbuild/msbuild-tasks.md)