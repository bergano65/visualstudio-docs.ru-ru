---
title: Устранение неполадок, связанных с нацеливанием платформы .NET Framework | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ae55e34f929acca6c708dfc39477f3bd6546f53f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703786"
---
# <a name="troubleshooting-net-framework-targeting-errors"></a>Устранение неполадок, связанных с настройкой для определенных версий платформы .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе описаны ошибки MSBuild, которые могут возникнуть из-за проблем со ссылками, и методы устранения этих ошибок.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Вы используете ссылку на проект или сборку, которая нацелена на другую версию .NET Framework  
 Вы можете использовать в приложениях ссылки на проекты или сборки, нацеленные на другие версии платформы [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Например, можно создать приложение для работы с клиентскими профилями [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)], которое ссылается на сборку, нацеленную на версию .NET Framework 2.0. Но если вы создаете проект, нацеленный на более раннюю версию [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], в нем нельзя использовать ссылки на проекты или сборки, нацеленные на клиентский профиль для [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] или [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)]. Чтобы устранить эту ошибку, ваше приложение должно быть нацелено на профили, которые совместимы с профилями, для работы с которыми предназначены проекты или сборки, на которые, в свою очередь, ссылается ваше приложение.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Вы перенацелили проект на другую версию платформы .NET Framework  
 Когда вы изменяете для приложения целевую версию [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], Visual Studio изменяет некоторые ссылки, но остальные нужно обновить вручную. Например, одна из указанных выше ошибок может возникать при перенацеливании приложения на [!INCLUDE[net_v35SP1_long](../includes/net-v35sp1-long-md.md)], если это приложение использует ресурсы или параметры, основанные на клиентских профилях для [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)].  
  
 Чтобы решить проблему с настройками приложения, откройте **обозреватель решений**, выберите **Показать все файлы**, а затем измените файл app.config в XML-редакторе Visual Studio. Установите здесь в параметрах соответствующую версию платформы .NET Framework. Например, вы можете изменить значение версии с 4.0.0.0 на 2.0.0.0. Аналогичным образом для приложения с добавленными ресурсами откройте **обозреватель решений**, нажмите кнопку **Показать все файлы**, затем разверните **Мой проект** (Visual Basic) или **Свойства** (C#) и измените файл Resources.resx в XML-редакторе Visual Studio. Замените здесь значение версии с 4.0.0.0 на 2.0.0.0.  
  
 Если приложение содержит ресурсы (например, значки или растровые изображения) или параметры (например, строки подключения к данным), для устранения этой ошибки удалите все элементы на странице **Параметры** в **конструкторе проектов**, а затем заново добавьте все необходимые настройки.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Вы перенацелили проект на другую версию платформы .NET Framework, а ссылки не могут разрешиться  
 Если вы перенацеливаете проект на другую версию [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], ссылки в некоторых случаях не будут правильно разрешаться. Чаще всего эта проблема связана с использованием полных ссылок на сборки. Для ее устранения можно удалить все ссылки, которые не могут разрешиться, и добавить их в проект заново. Также вы можете вручную изменить ссылки в файле проекта. Прежде всего следует удалить все ссылки, которые имеют такую форму:  
  
```  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Затем их нужно заменить ссылками в простой форме:  
  
```  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
> После этого закройте проект, повторно откройте и перестройте его, чтобы все ссылки наверняка разрешились правильно.  
  
## <a name="see-also"></a>См. также:  
 [Как ориентироваться на версию .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Профиль клиента .NET Framework](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)   
 [Выбор конкретной версии .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md)
