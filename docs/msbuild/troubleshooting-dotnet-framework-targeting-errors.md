---
title: Устранение неполадок, связанных с нацеливанием платформы .NET Framework | Документация Майкрософт
description: Сведения об ошибках MSBuild, которые могут возникнуть из-за проблем со ссылками, и о методах устранения этих ошибок.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 7b4e6f14eb5ba771ff83b0aa5fedc8ae261ca69d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902630"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>Устранение неполадок, связанных с настройкой для определенных версий платформы .NET Framework

В этом разделе описаны ошибки MSBuild, которые могут возникнуть из-за проблем со ссылками, и методы устранения этих ошибок.

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Используется ссылка на проект или сборку, которая нацелена на другую версию .NET Framework

 Разработчики могут создавать приложения, которые ссылаются на проекты или сборки, предназначенные для других версий платформы .NET Framework. Например, можно создать приложение для работы с клиентскими профилями .NET Framework 4, которое ссылается на сборку, ориентированную на .NET Framework 2.0. Но если вы создаете проект, ориентированный на более раннюю версию .NET Framework, в нем невозможно использовать ссылки на проекты или сборки, ориентированные на клиентский профиль .NET Framework 4 или саму платформу .NET Framework 4. Чтобы устранить эту ошибку, ваше приложение должно быть нацелено на профили, которые совместимы с профилями, для работы с которыми предназначены проекты или сборки, на которые, в свою очередь, ссылается ваше приложение.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Проект перенацелен на другую версию платформы .NET Framework

 Когда вы изменяете для приложения целевую версию .NET Framework, Visual Studio изменяет некоторые ссылки, но остальные нужно обновить вручную. Например, одна из указанных выше ошибок может возникать при перенацеливании приложения на .NET Framework 3.5 с пакетом обновления 1, если это приложение использует ресурсы или параметры, основанные на клиентском профиле для .NET Framework 4.

 Чтобы решить проблему с настройками приложения, откройте **обозреватель решений**, выберите **Показать все файлы**, а затем измените файл *app.config* в XML-редакторе Visual Studio. Установите здесь в параметрах соответствующую версию платформы .NET Framework. Например, вы можете изменить значение версии с 4.0.0.0 на 2.0.0.0. Аналогичным образом для приложения с добавленными ресурсами откройте **обозреватель решений**, нажмите кнопку **Показать все файлы**, затем разверните **Мой проект** (Visual Basic) или **Свойства** (C#) и измените файл *Resources.resx* в XML-редакторе Visual Studio. Замените здесь значение версии с 4.0.0.0 на 2.0.0.0.

 Если приложение содержит ресурсы (например, значки или растровые изображения) или параметры (например, строки подключения к данным), для устранения этой ошибки удалите все элементы на странице **Параметры** в **конструкторе проектов**, а затем заново добавьте все необходимые настройки.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Проект перенацелен на другую версию платформы .NET Framework, а ссылки не разрешаются

 Если вы ориентируете проект на другую версию .NET Framework, ссылки в некоторых случаях будут разрешаться неправильно. Чаще всего эта проблема связана с использованием полных ссылок на сборки. Для ее устранения можно удалить все ссылки, которые не могут разрешиться, и добавить их в проект заново. Также вы можете вручную изменить ссылки в файле проекта. Прежде всего следует удалить все ссылки, которые имеют такую форму:

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 Затем их нужно заменить ссылками в простой форме:

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> После этого закройте проект, повторно откройте и перестройте его, чтобы все ссылки наверняка разрешились правильно.

## <a name="see-also"></a>См. также раздел

- [Практическое руководство. Определение целевой версии .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [.NET Framework (клиентский профиль)](/dotnet/framework/deployment/client-profile)
- [Общие сведения о настройке для платформы](../ide/visual-studio-multi-targeting-overview.md)
- [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md)
