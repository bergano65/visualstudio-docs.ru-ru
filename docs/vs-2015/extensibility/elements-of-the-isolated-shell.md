---
title: Элементы изолированной оболочки | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e567fc212b9981d925fc11e8e0ae48132b3b05bf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816818"
---
# <a name="elements-of-the-isolated-shell"></a>Элементы изолированной оболочки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно изменить параметры реестра, параметры времени выполнения и точка входа приложения приложения изолированной оболочки и его .vsct, .pkgdef, and.pkgundef файлы.  
  
## <a name="registry-settings"></a>Параметры реестра  
 Измените параметры реестра для приложений изолированной оболочки, .pkgdef и .pkgundef файлы. При запуске приложения, параметры реестра определены в следующей последовательности:  
  
 При запуске приложения, параметры реестра определены в следующей последовательности:  
  
1.  Создать раздел реестра для приложения.  
  
2.  Обновляется реестр из pkgdef-файл приложения путем определения указанного разделы и записи.  
  
3.  Для каждого пакета, который является частью приложения обновляется реестр из pkgdef-файл этого пакета. Каждый пакет определяется в pkgdef-файл приложения $RootKey$ \Packages\\{*vsPackageGuid*} ключа для пакета.  
  
4.  Обновить реестр из AppEnvConfig.pkgdef и BaseConfig.pkgdef в *путь установки Visual Studio SDK*\Common7\IDE\ShellExtensions\Platform каталога. Эти файлы являются частью Visual Studio, а также частью распространяемый пакет оболочки Visual Studio (изолированный режим).  
  
5.  Обновляется реестр из файла .pkgundef приложения путем удаления указанного разделы и записи.  
  
## <a name="run-time-settings"></a>Параметры времени выполнения  
 Когда пользователь запускает приложение изолированной оболочки, она вызывает начальную точку входа оболочки Visual Studio. Определенные параметры приложения при запуске приложения, следующим образом:  
  
1. Оболочка Visual Studio проверяет реестр приложения для конкретных ключей. Если параметр для ключа в вызове начальную точку входа, это значение переопределяет значение в реестре.  
  
2. Если ни реестра, ни операция точки параметр задает значение параметра, то используется значение по умолчанию для параметра.  
  
   Когда пользователь запускает приложение из командной строки, оболочки Visual Studio, которая обрабатывает их таким же образом, выполняющий Devenv передаются все параметры командной строки. Дополнительные сведения о параметры команды Devenv, см. в разделе [командной строки devenv](../ide/reference/devenv-command-line-switches.md) и [переключателей командной строки Devenv для разработки VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Дополнительные сведения о как пакет регистрирует для параметров командной строки, см. в разделе [добавления переключателей командной строки](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Начальную точку входа  
 Файл Appenvstub.dll содержит точки входа для доступа к изолированной оболочки. При запуске приложения, он вызывает начала записи точки из Appenvstub.dll.  
  
 Можно изменить поведение приложения, изменив значение последнего параметра, передаваемое начальную точку входа. Дополнительные сведения см. в разделе [изолированной оболочки запись точки параметров (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>. Файл Vsct  
 Vsct-файл позволяет указать, какие стандартные элементы пользовательского интерфейса Visual Studio доступны в приложении. Дополнительные сведения см. в разделе [. Файлы Vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>. Файл Pkgundef  
 Когда приложение установлено на компьютере, на котором уже установлен Visual Studio, Visual Studio записи реестра копия для приложения. По умолчанию приложение использует пакеты VSPackage, который был установлен на компьютере. Файла .pkgundef позволяет исключить записи реестра для удаления конкретных элементов оболочки Visual Studio или расширения из приложения. Дополнительные сведения см. в разделе [. Файлы Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Файла .pkgundef позволяет исключить записи реестра для удаления конкретных элементов оболочки Visual Studio или расширения из приложения. Дополнительные сведения см. в разделе [. Файлы Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Набор идентификаторов GUID, которые вы можете исключить пакета перечислены в [пакет идентификаторов GUID из функции Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>. Файл pkgdef  
 Файл pkgdef позволяет определять записи реестра для приложения, устанавливаемые при установке приложения. Описание pkgdef-файл и список записей реестра, которые использует оболочка Visual Studio, см. в разделе [. Файлов pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Строки подстановки  
 Строки подстановки, используемые в файлах .pkgdef и .pkgundef, перечислены в [использовать строки подстановки в. Pkgdef и. Файлы Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Другие параметры  
 Если ваше приложение изолированной оболочки, зависит от Microsoft.VisualStudio.GraphModel.dll, необходимо добавить следующее перенаправление привязки в файле .config приложения изолированной оболочки:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```

