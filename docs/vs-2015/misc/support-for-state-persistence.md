---
title: Поддержка сохраняемости состояния | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state persistence, managed package framework support
- managed package framework, state persistence support
- state, persistence
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
manager: jillfra
ms.openlocfilehash: 6dc542d2e410b79a21e436a1881c06bd3cc4eef8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434323"
---
# <a name="support-for-state-persistence"></a>Поддержка сохранения состояния
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] может поддерживать состояние общих объектов. Например, свойства решения и проекта сохраняются в файлах решения и проекта и восстанавливаются из них. Параметры пользователя можно экспортировать в файлы параметров и импортировать из них.  
  
 Пакеты VSPackage обычно зависят от локального хранилища: в системном реестре или в папке данных приложения для текущего пользователя или компьютера. Значения, для которых требуется небольшой объем пространства для хранения, такие как целые числа и строки, обычно хранятся в системном реестре. Значения, требующие большого объема пространства для хранения, например точечные рисунки, сохраняются в файле. Путь к файлу может быть сохранен в системном реестре. Механизм сохраняемости должен иметь разрешение на доступ к локальному хранилищу.  
  
## <a name="support-for-locating-local-storage"></a>Поддержка обнаружения локального хранилища  
 <xref:Microsoft.VisualStudio.Shell.Package>Класс обеспечивает поддержку обнаружения сведений о состоянии в системном реестре или в папке данных приложения для текущего пользователя или компьютера.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Возвращает путь к корню реестра локального компьютера для, например [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0exp.  
  
 Локальный корень реестра получен из <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> службы. Если он недоступен, он получается из <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> атрибута VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Возвращает путь к корневому каталогу реестра текущего пользователя для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , например HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0exp.  
  
 Локальный корень реестра получен из <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> службы. Если он недоступен, он получается из атрибута Дефаултлокалрегистрирут пакета VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Возвращает путь к каталогу, который служит общим репозиторием для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] данных текущего перемещающегося пользователя, например C:\Documents and Settings \\ *йоураккаунтнаме*\Application Data\Microsoft\VisualStudio\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Возвращает путь к каталогу, который служит общим репозиторием для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] данных текущего пользователя, не перемещающегося в роуминге, например C:\Documents and Settings \\ *йоураккаунтнаме*\Local Settings\Application Data\Microsoft\VisualStudio\8.0Exp.  
  
## <a name="see-also"></a>См. также:  
 [Состояние VSPackage](../misc/vspackage-state.md)