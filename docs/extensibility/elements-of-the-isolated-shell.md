---
title: "Элементы изолированной оболочки | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Оболочка Visual Studio, в изолированном режиме"
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Элементы изолированной оболочки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно изменить параметры реестра, настройки времени выполнения и точка входа в приложение изолированной оболочки приложения и его .vsct, .pkgdef, and.pkgundef файлов.  
  
## Параметры реестра  
 .pkgdef и файлы .pkgundef изменить параметры реестра для приложения изолированной среды. При запуске приложения, параметры реестра определены в следующей последовательности:  
  
 При запуске приложения, параметры реестра определены в следующей последовательности:  
  
1.  Создать раздел реестра для приложения.  
  
2.  Определив указанных разделов и записей реестра обновляется pkgdef\-файл приложения.  
  
3.  Для каждого пакета, который является частью приложения реестр обновляется pkgdef\-файл пакета. Каждый пакет определяется в pkgdef\-файл приложения $RootKey$ \\Packages\\ {*vsPackageGuid*} ключа для пакета.  
  
4.  Обновить реестр из AppEnvConfig.pkgdef и BaseConfig.pkgdef в *путь установки Visual Studio SDK*\\Common7\\IDE\\ShellExtensions\\Platform каталога. Эти файлы являются частью Visual Studio, а также часть распространяемый пакет оболочки Visual Studio \(изолированный режим\).  
  
5.  Обновить реестр из файла .pkgundef приложения путем удаления указанных разделов и записей.  
  
## Параметры времени выполнения  
 Когда пользователь запускает приложения изолированной среды, он вызывает начальную точку входа оболочки Visual Studio. Параметры приложения, определяются при запуске приложения, как показано ниже:  
  
1.  Оболочка Visual Studio проверяет реестр приложения для определенных ключей. Если в вызове начальную точку входа указан параметр для ключа, это значение переопределяет значение в реестре.  
  
2.  Если запись ни реестра точки параметр задает значение параметра, то используется значение по умолчанию для параметра.  
  
 При запуске приложения из командной строки, все параметры командной строки передаются в оболочке Visual Studio, которая обрабатывает их таким же образом, выполняющий Devenv. Дополнительные сведения о параметрах команды Devenv см. в разделе [Параметры командной строки для команды Devenv](../ide/reference/devenv-command-line-switches.md) и [Параметры командной строки devenv для разработки VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Дополнительные сведения о как пакет регистрирует для командной строки см. в разделе [Добавление параметров командной строки](../extensibility/adding-command-line-switches.md).  
  
## Начальную точку входа  
 Файл Appenvstub.dll содержит точки входа для доступа к изолированной оболочки. При запуске приложения, он вызывает начала записи точки из Appenvstub.dll.  
  
 Можно изменить поведение приложения, изменив значение последний параметр, передаваемый начальную точку входа. Для получения дополнительной информации см. [Параметры точки входа изолированной оболочки \(C\+\+\)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## . Файл Vsct  
 Файл .vsct позволяет указать, какие стандартных элементов пользовательского интерфейса Visual Studio доступны в приложении. Дополнительные сведения см. в разделе [. Vsct\-файлы](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## . Файл Pkgundef  
 Если приложение установлено на компьютере, на котором уже установлена среда Visual Studio, записи реестра Visual Studio копия приложения. По умолчанию приложение использует пакеты VSPackage, который был установлен на компьютере. Файл .pkgundef позволяет исключить записи реестра для удаления конкретных элементов оболочки Visual Studio или расширения из приложения. Дополнительные сведения см. в разделе [. Pkgundef файлы](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Файл .pkgundef позволяет исключить записи реестра для удаления конкретных элементов оболочки Visual Studio или расширения из приложения. Дополнительные сведения см. в разделе [. Pkgundef файлы](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Набор идентификаторов GUID, можно исключить пакета перечислены в [GUID пакета возможностей Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## . Файл pkgdef  
 Файл pkgdef позволяет определять записи реестра для приложения, которые задаются при установке приложения. Описание pkgdef\-файл и список записей реестра, используемые оболочкой Visual Studio см. в разделе [. Файлы pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## Строки подстановки  
 Строки подстановки, используемые в файлах .pkgdef и .pkgundef перечислены в [Строки подстановки, используемые в. Pkgdef и. Pkgundef файлы](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## Другие параметры  
 Если приложение изолированной оболочки, зависит от Microsoft.VisualStudio.GraphModel.dll, необходимо добавить следующие перенаправления привязки в файл .config приложения изолированной среды:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```