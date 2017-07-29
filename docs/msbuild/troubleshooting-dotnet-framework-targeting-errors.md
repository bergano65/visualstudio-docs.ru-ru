---
title: "Устранение неполадок, связанных с нацеливанием платформы .NET Framework | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 29
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 8bf0b097be929b30627e0f1139c6e0b145933ab4
ms.openlocfilehash: 0fb16d2625bde02a6370a1f06483d7b486c46f4a
ms.contentlocale: ru-ru
ms.lasthandoff: 05/26/2017

---
# <a name="troubleshooting-net-framework-targeting-errors"></a>Устранение неполадок, связанных с настройкой для определенных версий платформы .NET Framework
В этом разделе описаны ошибки MSBuild, которые могут возникнуть из-за проблем со ссылками, и методы устранения этих ошибок.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Вы используете ссылку на проект или сборку, которая нацелена на другую версию .NET Framework  
 Вы можете использовать в приложениях ссылки на проекты или сборки, нацеленные на другие версии платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Например, можно создать приложение для работы с клиентскими профилями [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)], которое ссылается на сборку, нацеленную на версию .NET Framework 2.0. Но если вы создаете проект, нацеленный на более раннюю версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], в нем нельзя использовать ссылки на проекты или сборки, нацеленные на клиентский профиль для [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] или [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]. Чтобы устранить эту ошибку, ваше приложение должно быть нацелено на профили, которые совместимы с профилями, для работы с которыми предназначены проекты или сборки, на которые, в свою очередь, ссылается ваше приложение.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Вы перенацелили проект на другую версию платформы .NET Framework  
 Когда вы изменяете для приложения целевую версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio изменяет некоторые ссылки, но остальные нужно обновить вручную. Например, одна из указанных выше ошибок может возникать при перенацеливании приложения на [!INCLUDE[net_v35SP1_long](../msbuild/includes/net_v35sp1_long_md.md)], если это приложение использует ресурсы или параметры, основанные на клиентских профилях для [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)].  
  
 Чтобы решить проблему с настройками приложения, откройте **обозреватель решений**, выберите **Показать все файлы**, а затем измените файл app.config в XML-редакторе Visual Studio. Установите здесь в параметрах соответствующую версию платформы .NET Framework. Например, вы можете изменить значение версии с 4.0.0.0 на 2.0.0.0. Аналогичным образом, для приложения с добавленными ресурсами откройте **обозреватель решений**, нажмите кнопку **Показать все файлы**, затем разверните **Мой проект** (для Visual Basic) или **Свойства** (для C#) и измените файл Resources.resx в XML-редакторе Visual Studio. Замените здесь значение версии с 4.0.0.0 на 2.0.0.0.  
  
 Если приложение содержит ресурсы (например, значки или растровые изображения) или параметры (например, строки подключения к данным), для устранения этой ошибки удалите все элементы на странице **Параметры** в **конструкторе проектов**, а затем заново добавьте все необходимые настройки.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Вы перенацелили проект на другую версию платформы .NET Framework, а ссылки не могут разрешиться  
 Если вы перенацеливаете проект на другую версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], ссылки в некоторых случаях не будут правильно разрешаться. Чаще всего эта проблема связана с использованием полных ссылок на сборки. Для ее устранения можно удалить все ссылки, которые не могут разрешиться, и добавить их в проект заново. Также вы можете вручную изменить ссылки в файле проекта. Прежде всего следует удалить все ссылки, которые имеют такую форму:  
  
```xml  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Затем их нужно заменить ссылками в простой форме:  
  
```xml  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
>  После этого закройте проект, повторно откройте и перестройте его, чтобы все ссылки наверняка разрешились правильно.  
  
## <a name="see-also"></a>См. также  
 [How to: Target a Version of the .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)  (Практическое руководство. Нацеливание на определенную версию .NET Framework)  
 [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile)  (Профиль клиента .NET Framework)  
 [Targeting a Specific .NET Framework Version](../ide/targeting-a-specific-dotnet-framework-version.md)  (Нацеливание на определенную версию .NET Framework)  
 [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md)
