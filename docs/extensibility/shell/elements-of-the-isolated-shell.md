---
title: "Элементы изолированной оболочки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 82379a840010ebae434f8ad1a03c12793fe10ec5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="elements-of-the-isolated-shell"></a>Элементы изолированной оболочки
Можно изменить параметры реестра, настройки времени выполнения и точка входа приложения изолированной оболочки приложения и его .vsct, .pkgdef, and.pkgundef файлов.  
  
## <a name="registry-settings"></a>Параметры реестра  
 .pkgdef и файлы .pkgundef изменить параметры реестра для приложения изолированной оболочки. При запуске приложения, параметры реестра определяются в следующей последовательности:  
  
 При запуске приложения, параметры реестра определяются в следующей последовательности:  
  
1.  Создать раздел реестра для приложения.  
  
2.  Путем определения указанных разделов и записей реестра обновляется pkgdef-файл приложения.  
  
3.  Для каждого пакета, который является частью приложения обновляется реестр pkgdef-файл из этого пакета. Каждый пакет определяется в pkgdef-файл приложения $RootKey$ \Packages\\{*vsPackageGuid*} ключа для пакета.  
  
4.  Обновить реестр из AppEnvConfig.pkgdef и BaseConfig.pkgdef в *путь установки Visual Studio SDK*\Common7\IDE\ShellExtensions\Platform каталога. Эти файлы являются частью Visual Studio, а также частью распространяемого пакета оболочки Visual Studio (изолированный режим).  
  
5.  Обновить реестр из файла .pkgundef приложения путем удаления указанных разделов и записи.  
  
## <a name="run-time-settings"></a>Параметры времени выполнения  
 Когда пользователь запускает приложение изолированной оболочки, он вызывает начальную точку входа оболочки Visual Studio. Определенные параметры приложения при запуске приложения, как показано ниже:  
  
1.  Оболочка Visual Studio проверяет реестр приложения для конкретных ключей. Если в вызове начальную точку входа указано значение для ключа, это значение переопределяет значение в реестре.  
  
2.  Если запись ни реестра точки параметр задает значение параметра, то используется значение по умолчанию для параметра.  
  
 Когда пользователь запускает приложение из командной строки, все параметры командной строки передаются оболочки Visual Studio, которая обрабатывает их таким же образом, выполняющий Devenv. Дополнительные сведения о параметрах Devenv см. в разделе [командной строки devenv](../../ide/reference/devenv-command-line-switches.md) и [переключателей командной строки Devenv для разработки VSPackage](../devenv-command-line-switches-for-vspackage-development.md). Дополнительные сведения о как пакет регистрирует для параметров командной строки см. в разделе [добавления переключателей командной строки](../adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Начальную точку входа  
 Файл Appenvstub.dll содержит точки входа для доступа к изолированной оболочки. При запуске приложения, он вызывает начала записи точки из Appenvstub.dll.  
  
 Можно изменить поведение приложения, изменив значение последнего параметра, передаваемое начальную точку входа. Дополнительные сведения см. в разделе [изолированной оболочки запись точки параметров (C++)](isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>. Vsct-файла  
 Vsct-файле позволяет указать, какие стандартные элементы пользовательского интерфейса Visual Studio доступны в приложении. Дополнительные сведения см. в разделе [. Файлы Vsct](modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>. Файл pkgundef-файлов  
 Если приложение установлено на компьютере, на котором уже установлена среда Visual Studio, записи реестра Visual Studio копия для приложения. По умолчанию приложение использует пакеты VSPackage, которые уже установлены на компьютере. Файл .pkgundef позволяет исключить записи реестра, чтобы удалить конкретные элементы оболочки Visual Studio или расширения из приложения. Дополнительные сведения см. в разделе [. Файлы pkgundef-файлов](modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Файл .pkgundef позволяет исключить записи реестра, чтобы удалить конкретные элементы оболочки Visual Studio или расширения из приложения. Дополнительные сведения см. в разделе [. Файлы pkgundef-файлов](modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Набор идентификаторов GUID, можно исключить пакета перечислены в [пакета GUID из функции Visual Studio](package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>. Файл pkgdef  
 Файл pkgdef позволяет определить записи реестра для приложения, устанавливаемые при установке приложения. Описание pkgdef-файл и список записей реестра, используемые оболочкой Visual Studio см. в разделе [. Файлах pkgdef](modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Строки подстановки  
 Строки подстановки, используемые в файлах .pkgdef и .pkgundef, перечислены в [использовать строки подстановки в. Pkgdef и. Файлы pkgundef-файлов](substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Другие параметры  
 Если приложение изолированной оболочки зависит от Microsoft.VisualStudio.GraphModel.dll, необходимо добавить следующее перенаправление привязки в файле .config приложения изолированной оболочки:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```